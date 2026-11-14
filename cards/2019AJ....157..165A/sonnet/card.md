# A Tail Structure Associated with a Protoplanetary Disk around SU Aurigae

`2019AJ....157..165A` | The Astronomical Journal 2019 | first author: Akiyama, Eiji | arXiv: 1902.10306 | DOI: 10.3847/1538-3881/ab0ae4

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Is there a CO (J=2-1) gas counterpart to the tail-like structure seen in scattered light around the SU Aur disk, is it kinematically connected to the disk, and what could have produced it?  
  > "Here we report the discovery of the counterpart of the tail-like structure in CO gas extending more than 1000 au long." (abstract)
- Target **SU Aurigae**: coordinates cross mark (zero point for curves): R.A. 04h55m59.73s, Dec. 30d34m03.32s (as printed, with conversion noise)  
  > "158 ± 2 pc (Gaia Collaboration et al. 2018)" (1. INTRODUCTION); "The cross mark (R.A. 04h55m59 [′′] .73, Dec. 30 [◦] 34 [′] 03 [′′] .32)" (Figure 1 caption); z/distance 158 ± 2 pc  
  > "158 ± 2 pc (Gaia Collaboration et al. 2018)" (1. INTRODUCTION); "The cross mark (R.A. 04h55m59 [′′] .73, Dec. 30 [◦] 34 [′] 03 [′′] .32)" (Figure 1 caption); distance from Gaia Collaboration et al. 2018  
  > "158 ± 2 pc (Gaia Collaboration et al. 2018)" (1. INTRODUCTION); "The cross mark (R.A. 04h55m59 [′′] .73, Dec. 30 [◦] 34 [′] 03 [′′] .32)" (Figure 1 caption)

## Data provenance

- ALMA projects: 2013.1.00426.S
- bands: Band 6 (1.3 mm)  
  > "Observations were performed on July 19 and August 8 in 2015 at Band 6, containing 36 and 40 12-m antennas, respectively." (2. OBSERVATIONS AND DATA REDUCTION)
- frequencies and spectral setup: CO(2-1) at 230.538 GHz plus nearby 1.3 mm continuum; channel width 30.518 kHz (0.04 km/s)  
  > "The spectral resolution was set up to be 30.518 kHz, corresponding to 0.04 km s [−][1] ." (2. OBSERVATIONS AND DATA REDUCTION)
- continuum bandwidth: _not stated_
- arrays: 12-m antennas (36 and 40)  
  > "containing 36 and 40 12-m antennas, respectively." (2. OBSERVATIONS AND DATA REDUCTION)
- configurations: _not stated_
- baselines: 15 m to 1.57 km  
  > "The baseline length of the observed array configuration spanned from 15 m to 1.57 km" (2. OBSERVATIONS AND DATA REDUCTION)
- angular resolution: 0.235 x 0.356 arcsec synthesized beam  
  > "the synthesized beam of 0.”235 × 0.”356 is obtained." (2. OBSERVATIONS AND DATA REDUCTION)
- max recoverable scale: 11 arcsec  
  > "resulting in a maximum recoverable size of 11 arcsec." (2. OBSERVATIONS AND DATA REDUCTION)
- sensitivity: _not stated_
- time on source: 14.5 minutes after flagging  
  > "integrated time on source of 14.5 minutes after data flagging" (3. RESULTS)
- observing dates: July 19 and August 8, 2015  
  > "Observations were performed on July 19 and August 8 in 2015 at Band 6" (2. OBSERVATIONS AND DATA REDUCTION)
- pi or archival as stated: archival  
  > "The ALMA archival data (2013.1.00426.S) are used in the paper." (2. OBSERVATIONS AND DATA REDUCTION)
- Line: CO J=2-1 (230.538 GHz)
- Other facility **Subaru (SEEDS) H-band polarimetry**: Scattered-light tail of small dust grains, compared with the CO tail  
  > "we conducted H-band polarimetry observations toward protoplanetary disk around SU Aur" (1. INTRODUCTION)
- External data: Subaru H-band polarized intensity of the tail, overlaid on CO map  
  > "with Subaru H-band polarized intensity (PI) (de Leon et al. 2015) in dark color contour" (Figure 2 caption) [from de Leon et al. 2015]
- External data: Tail dust mass ~6e-8 Msun  
  > "the dust mass in the tail-like structure is estimated to be ∼ 6 × 10 [−][8] M ⊙ (de Leon et al. 2015)" (3. RESULTS) [from de Leon et al. 2015]
- External data: Disk mass 9.0e-2 Msun (gas-to-dust 100) from PdBI  
  > "the disk mass can be 9.0 × 10 [−][2] M ⊙ under assumption of gas to dust ratio of 100 (Ricci et al. 2010)" (4.2. Origin of the Tail-Like Structure) [from Ricci et al. 2010]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.3.1  
  > "CLEAN task provided in CASA version 4.3.1 package" (2. OBSERVATIONS AND DATA REDUCTION)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration (phase and amplitude) on continuum, stopped when rms reached minimum; table applied to CO line data  
  > "We checked rms noise level at each round by generating the image and stopped selfcalibration with amplitude and phase correction when the rms noise level reached minimum." (2. OBSERVATIONS AND DATA REDUCTION)

### Imaging

- task: CLEAN in CASA 4.3.1  
  > "The Band 6 data were imaged using the CLEAN task provided in CASA version 4.3.1 package" (2. OBSERVATIONS AND DATA REDUCTION)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 1.5  
  > "generate the images with a robust parameter of 1.5 in Briggs weighting" (2. OBSERVATIONS AND DATA REDUCTION)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Applied to make sensitivity uniform over the FoV  
  > "the sensitivity of the primary beam is scaled by primary beam correction task so that the sensitivity becomes uniform in the entire field of view (FoV)." (2. OBSERVATIONS AND DATA REDUCTION)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.235 x 0.356 arcsec  
  > "the synthesized beam of 0.”235 × 0.”356 is obtained." (2. OBSERVATIONS AND DATA REDUCTION)
- final rms: 28 mJy/beam km/s (moment 0); continuum 1 sigma 0.135 mJy/beam  
  > "The resultant rms is 28 mJy beam [−][1] km s [−][1] in the" (3. RESULTS); "the contours are 0.135 mJy beam [−][1] (1 σ) × [5, 10, 20, 30, 40, 50, 60]" (Figure 2 caption)

### Inherited from earlier work

- Keplerian disk model for velocity residual  
  > "Detail description can be found in the Appendix in (Isella et al. 2007)." (4.1. Kinematic Structure of Star and Disk System) [from Isella et al. 2007]

### Not stated but needed to reproduce (our reading)

- Calibrator for flux scale and the flux uncertainty
- Pipeline vs manual calibration and whether delivered products were used
- Self-calibration solution intervals and number of rounds
- Continuum-subtraction method and line-free channels
- Image size, cell size, masking, clean threshold, and deconvolver
- Whether the image cube was smoothed or rebinned to ~0.3 km/s channels
- Moment-map clipping beyond 30 mJy/beam and the channel range used for moment 0
- Keplerian model parameters (stellar mass, inclination, PA, outer radius)
- Tail extraction path/line for Figure 3b,c
- Brightness temperature calculation details

## Analysis recipe

1. **Image the CO(2-1) cube**: Self-calibrate on continuum, apply tables to line data, CLEAN with Briggs weighting, primary beam correction  
  > "Then we apply the calibration table to the CO (J=2–1) line data and generate the images with a robust parameter of 1.5 in Briggs weighting." (2. OBSERVATIONS AND DATA REDUCTION)
   - software: CASA
   - parameter: robust = 1.5  
  > "a robust parameter of 1.5 in Briggs weighting" (2. OBSERVATIONS AND DATA REDUCTION)
   - fitting: _not stated_
   - validation: Self-calibration stopped when rms minimum  
  > "stopped selfcalibration with amplitude and phase correction when the rms noise level reached minimum." (2. OBSERVATIONS AND DATA REDUCTION)
2. **Make moment maps, channel maps and velocity profiles**: Moments 0,1,2 from channels 1.87-10.87 km/s above 30 mJy/beam; velocity and dispersion curves along the tail; disk spectrum within 1.2 arcsec radius  
  > "The 1st and 2nd moment maps is created using velocity channels from 1.87 to 10.87 km s [−][1] and emission above 30 mJy beam [−][1] ." (Figure 1 caption)
   - fitting: _not stated_
   - validation: _not stated_
3. **Subtract Keplerian disk model from moment 1**: Simple flat Keplerian disk model in same orientation, subtracted from observed moment 1 map in the disk region  
  > "We made a simple keplerian disk model in the same orientation with the observed disk component and then computed the residual after subtracting the model from the observed moment 1 map." (4.1. Kinematic Structure of Star and Disk System)
   - assumption: Flat disk geometry, circular orbits  
  > "We also assume the disk has flat geometry in the model." (4.1. Kinematic Structure of Star and Disk System)
   - fitting: _not stated_
   - validation: Southern disk residual ~zero, supporting Keplerian rotation  
  > "the motion in the southern part of the disk is almost cancelled by the model counterpart, resulting in approximately zero velocity." (4.1. Kinematic Structure of Star and Disk System)
4. **Estimate tail brightness temperature**: From a channel-map panel with beam size and CO(2-1) rest frequency  
  > "We selected a panel detecting tail-like structure from the channel map and applied the beam size and the rest frequency in CO (J=2–1) line." (4.2. Origin of the Tail-Like Structure)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3.1: CLEAN imaging, self-calibration  
  > "CLEAN task provided in CASA version 4.3.1 package" (2. OBSERVATIONS AND DATA REDUCTION)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Tail length in CO | >1000 | not stated | au | 2 | a tail-like structure more than 1000 au long extending from the northern part of the disk body to the southwest direction |
| Disk peak integrated intensity | 400 | rms 28 | mJy/beam km/s | 2 | The disk component has a peak intensity of 400 mJy beam [−][1] km s [−][1] in CO (J=2–1) emission |
| 1.3 mm continuum peak | 850 | not stated | mJy/beam | 2 | whose peak intensity of 850 mJy beam [−][1] , as displayed in white contour |
| Systemic velocity | 5.8 | 0.3 | km/s | 2 | at 5.8 ± 0.3 km s [−][1] |
| Tail velocity dispersion | ~0.7 (disk ~2) | not stated | km/s | 2 | The tail component has a velocity dispersion of ∼ 0.7 km s [−][1] whereas the disk component has ∼ 2 km s [−][1] . |
| Tail brightness temperature | ~16 | not stated | K | 4 | the brightness temperature is about 16 K |

## Qualitative findings

- CO tail is red-shifted by 0.5-1 km/s from systemic velocity and connects smoothly with the northern disk; northern disk deviates from Keplerian rotation  
  > "Thus, the tail-like component is red shifted by 0.5 – 1 km s [−][1] from the systemic velocity of 5.8 km s [−][1] ." (3. RESULTS)
- Tail seen in CO and 0.1-1 micron dust but not in mm continuum  
  > "The results support that 0.1 – 1 µm-sized dust is well coupled with gas, while mm-sized dust is not." (3. RESULTS)

## Claim tuples

- H: Does the scattered-light tail have a CO gas counterpart connected to the disk? | E: CO(2-1) moment and channel maps from archival ALMA data | R: CO tail >1000 au at ~6.5 km/s connects smoothly to the northern disk | F: Disk and tail are physically and kinematically connected | **supported**
- H: Which mechanism produced the tail? | E: Keplerian residual plus comparison with published simulations | R: No random motion in disk; ejection less probable; intruder mass limit <2e-3 Msun | F: Collision with a gaseous blob or (sub)stellar intruder is most plausible; not conclusive | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Ejection of a planetary or brown dwarf mass object judged less probable since no random motion is detected in the disk  
  > "Since no random motion is detected in the disk but rather disk motion uniformly connects with the motion of the tail-like structure, it seems less probable." (4.2. Origin of the Tail-Like Structure)
- How they decided it was enough: _not stated_
- Limitation (authors): Tail reaches FoV edge; fan-shaped emission in the southwest may be artificial  
  > "Note that the fan-shaped emission seen in southwest region in the moment maps could possibly be artificial." (3. RESULTS)
- Caveat (inferred, ours): Mechanism discrimination is qualitative with no quantitative modeling of the data
- Caveat (inferred, ours): Tail truncated by primary beam edge, so its extent and kinematics are uncertain
- Caveat (inferred, ours): Possible contamination of the cloud/foreground by extended emission, and missing flux from interferometer filtering, not assessed
- Caveat (inferred, ours): Keplerian model parameters unspecified

## Reproducibility

- Data public (paper): Archival ALMA data 2013.1.00426.S  
  > "The ALMA archival data (2013.1.00426.S) are used in the paper." (2. OBSERVATIONS AND DATA REDUCTION)
- Products in archive: _not stated_
- Missing: Keplerian model parameters
- Missing: self-calibration details
- Missing: image/cell size and masks
- Missing: tail extraction path
- Data volume (inferred): ~50-100 GB raw for two executions with high spectral resolution
- Score (inferred): 3/5, Public data and basic imaging settings are given, but many parameters for imaging, modelling and profile extraction are missing.
- Rediscovery candidate: yes, Data are public and moment maps and the tail detection are reproducible, though some settings are missing.

## Links

- Method: Isella et al. 2007 (Keplerian disk model description)
- Companion: de Leon et al. 2015 (Subaru H-band detection of the tail)
- Related: SEEDS

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
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
  "facts": 67,
  "stated": 39,
  "rate": 0.582
 },
 "evidence_ok": true
}
```
