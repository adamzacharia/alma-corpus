# Planet-induced spirals in the circumbinary disk of GG Tauri A

`2020A&A...635L...9P` | Astronomy and Astrophysics 2020 | first author: Phuong, N. T. | arXiv: - | DOI: 10.1051/0004-6361/202037682

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Is there indirect evidence of planets in the circumbinary disk of GG Tau A, seen as spirals in CO(2-1)?  
  > "We searched for indirect evidence for planet formation in the multiple system GG Tau A, which harbors the most massive circumbinary disk among T Tauri stars." (abstract)
- Target **GG Tau A**: coordinates RA = 04:32:30.3448, Dec = 17:31:40.59 (J2000, ring center)  
  > "The reference of the coordinates, which corresponds to the GG Tau ring center, are RA = 04:32:30.3448 and Dec = 17:31:40.59 at epoch J2000.0." (2. Observations and data reduction); "The Gaia parallax indicates a distance of D = 150.1 ± 2.2 pc." (2. Observations and data reduction); z/distance 150.1 ± 2.2 pc  
  > "The reference of the coordinates, which corresponds to the GG Tau ring center, are RA = 04:32:30.3448 and Dec = 17:31:40.59 at epoch J2000.0." (2. Observations and data reduction); "The Gaia parallax indicates a distance of D = 150.1 ± 2.2 pc." (2. Observations and data reduction); distance from Gaia DR2 parallax of GG Tau Ba  
  > "The reference of the coordinates, which corresponds to the GG Tau ring center, are RA = 04:32:30.3448 and Dec = 17:31:40.59 at epoch J2000.0." (2. Observations and data reduction); "The Gaia parallax indicates a distance of D = 150.1 ± 2.2 pc." (2. Observations and data reduction)

## Data provenance

- ALMA projects: 2018.1.00532.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 1398 m  
  > "The projected baselines range from 15 m to 1398 m, and the total time on source is about three hours." (2. Observations and data reduction)
- angular resolution: 0.31'' x 0.25'' at PA 26.7 deg  
  > "The angular resolution is 0.31 [′′] × 0.25 [′′] at PA 26.7 [◦] ." (2. Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 1.35 mJy/beam (0.40 K); channel spacing 0.079 km/s, effective resolution 0.16 km/s  
  > "The rms noise level is 1.35 mJy beam [−][1], or 0.40 K at this resolution." (2. Observations and data reduction); "The channel spacing is 0.079 km s [−][1], and the effective spectral resolution is 0.16 km s [−][1] ." (2. Observations and data reduction)
- time on source: about three hours  
  > "The projected baselines range from 15 m to 1398 m, and the total time on source is about three hours." (2. Observations and data reduction)
- observing dates: November 8, 13, and 18, 2018; four scheduling blocks, 44 to 47 antennas  
  > "were carried on November 8, 13, and 18, 2018, with 44 to 47 useful antennas in four scheduling blocks." (2. Observations and data reduction)
- pi or archival as stated: PI Denis Alpizar, Cycle 6  
  > "ALMA observations of project 2018.1.00532.S (PI Denis Alpizar)" (2. Observations and data reduction)
- Line: CO 2-1 (not stated)
- Other facility **Gaia DR2**: proper motions and parallax distance of GG Tau Ba, adopted for GG Tau A  
  > "We assumed that the proper motions and distance of GG Tau A are those of GG Tau Ba." (2. Observations and data reduction)
- External data: Scale height H_c(r) = 17 × (r/200 au) from CO analysis (kinetic temperature 15 K), aspect ratio 0.085  
  > "We used a scale height H c ( r ) = 17 ×" (3. Results) [from Phuong et al. 2020]
- External data: CO(6-5) hot spot location and brightness (40 K) interpreted as an accreting protoplanet  
  > "The inner main spiral may take its origin near the location of the CO(6–5) hot spot that Dutrey et al. (2014) interpreted as" (3. Results) [from Dutrey et al. (2014)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "Data were calibrated in the CASA [1] software (Version 5.4.0) using the pipeline." (2. Observations and data reduction)
- casa version: 5.4.0  
  > "Data were calibrated in the CASA [1] software (Version 5.4.0) using the pipeline." (2. Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800 and J0423-0120 (flux and bandpass)  
  > "Quasars J0510+1800 and J0423−0120 were used for flux and bandpass calibration." (2. Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: Amplitude and phase self-cal on continuum, applied to line data  
  > "Amplitude and phase self-calibration was performed on the continuum signal, and the derived corrections were applied to the spectral line data." (2. Observations and data reduction)

### Imaging

- task: IMAGER in GILDAS  
  > "Imaging and deconvolution was made using the IMAGER program in GILDAS, with robust weighting." (2. Observations and data reduction)
- deconvolver: multiscale hogbom-like Clean, cleaned to rms noise  
  > "Deconvolution was made using the a multiscale _hogbom_ like Clean algorithm, and the images were cleaned down to the rms noise level." (2. Observations and data reduction)
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
- final beam: 0.31'' x 0.25'' at PA 26.7 deg  
  > "The angular resolution is 0.31 [′′] × 0.25 [′′] at PA 26.7 [◦] ." (2. Observations and data reduction)
- final rms: 1.35 mJy/beam (0.40 K)  
  > "The rms noise level is 1.35 mJy beam [−][1], or 0.40 K at this resolution." (2. Observations and data reduction)

### Inherited from earlier work

- Scale height and aspect ratio of the disk taken from earlier CO analysis  
  > "as derived from the CO analysis by Phuong et al." (3. Results) [from Phuong et al. 2020]
- Spiral wake prescription  
  > "we used the prescription of a spiral wave from Rafikov (2002) and Muto et al. (2012)." (3. Results) [from Rafikov (2002); Muto et al. (2012)]

### Not stated but needed to reproduce (our reading)

- robust value
- self-calibration solints and number of iterations
- clean masks, scales and threshold
- continuum-subtraction/line-free channels
- disk inclination used for deprojection
- how spirals were fitted (no statistical fit or goodness measure)
- exact method to rotate/project spiral and correct for layer height
- the Phuong et al. 2020 inputs
- rest frequency and continuum bandwidth

## Analysis recipe

1. **Image continuum and CO(2-1) and derive moment maps**: Calibrate with CASA pipeline, cvel to LSR, export to GILDAS, self-calibrate, image with IMAGER, make integrated and peak brightness maps, deproject and azimuthally average  
  > "exported through UVFITS format to the GILDAS [2] package for further data processing." (2. Observations and data reduction)
   - software: CASA, GILDAS
   - assumption: Proper motion and distance of GG Tau A are those of GG Tau Ba  
  > "We assumed that the proper motions and distance of GG Tau A are those of GG Tau Ba." (2. Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit planet-induced spiral wake to the CO peak brightness**: Linear spiral wake of Rafikov (2002)/Muto et al. (2012) with planet at hot spot; free parameter X (height of tau=1 layer in scale heights); rotated from disk PA of 7 deg  
  > "The only free parameter in our spiral fit was therefore the height of the τ = 1 layer in CO in scale height units along the spiral, X ." (3. Results)
   - parameter: planet at PA = 125 deg, r_c = 1.93'' (290 au); a = 3/2; b = 0.45; h_c = 0.085  
  > "The disk is in Keplerian rotation ( _a_ = 3 [�] 2) and the temperature was found to" (3. Results)
   - assumption: X independent of r  
  > "We assumed that X is independent of r ." (3. Results)
   - fitting: Visual comparison of model spirals with the peak brightness image; no formal fit  
  > "We found the shape to be sensitive to the value of _X_, but rather insensitive to those of _b_ and to the exact position of the planet." (3. Results)
   - validation: Comparison with spine of NW arm; SE arm only marginally reproduced  
  > "However, the SE arm is more marginally reproduced." (3. Results)
3. **Model additional spirals with outer planets**: Same parameters, shift planet position to match SE and SW spirals  
  > "A good model, using the same parameters as for GG Tau Ac except for the planet position, is obtained by locating GG Tau Ad at radius of ∼3.0 [′′] (450 au) and PA of ∼118 [◦]" (4. Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.0: pipeline calibration and cvel velocity regridding  
  > "Data were calibrated in the CASA [1] software (Version 5.4.0) using the pipeline." (2. Observations and data reduction)
- **GILDAS (IMAGER)** : imaging, deconvolution and self-calibration  
  > "Imaging and deconvolution was made using the IMAGER program in GILDAS, with robust weighting." (2. Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Best CO layer height X | 2.5 | not stated | scale heights | 2 | X = 2.5 provides an excellent match to the spine of the NW spiral arm. |
| NW arm peak brightness temperature | 16-18 | not stated | K | 1 | with a peak emission in the NW region T b,peak = 16−18 K |
| SE arm peak brightness temperature | 14-16 | not stated | K | 1 | with a maximum brightness temperature T b,peak = 14−16 K |
| Planet GG Tau Ad position | ~3.0'' (450 au), PA ~118 deg | not stated | arcsec, deg | 3 | GG Tau Ad at radius of ∼3.0 [′′] (450 au) and PA of ∼118 [◦] |
| Planet GG Tau Ae position | ~4.0'' (600 au), PA ~215 deg | not stated | arcsec, deg | 3 | located around 4.0 [′′] (600 au) and PA of ∼215 [◦] |

## Qualitative findings

- CO(2-1) shows spirals out to 5-6'' connected to the hot spot  
  > "revealing large spirals out to 5−6 [′′] that seem to be physically connected to the hot spot" (1. Introduction)

## Claim tuples

- H: The brightest spiral is launched by a planet at the hot spot | E: Fit linear spiral wake with planet at 290 au | R: X = 2.5 matches NW arm; SE arm marginal | F: A planet GG Tau Ac at the hot spot explains the NW spiral; its mass is Neptune-like or lower | **supported**
- H: Outer spirals are due to additional planets | E: Shift planet position in the same model | R: Planets at ~450 au and ~600 au reproduce the SE and SW spirals | F: One or more further planets near mean-motion resonances may exist | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Corotation or Lindblad torque reversal would predict a planet at the inner ring edge  
  > "would rather predict a final planet position located at the inner edge of the ring." (4. Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): SE arm only marginally reproduced by the model  
  > "However, the SE arm is more marginally reproduced." (3. Results)
- Caveat (inferred, ours): Spiral matching is by eye with no formal fit or uncertainties
- Caveat (inferred, ours): Planet masses are inferred only from the absence of a gap
- Caveat (inferred, ours): Planet positions are degenerate with X and are not unique
- Caveat (inferred, ours): Alternatives such as gravitational instability or tidal effects from GG Tau B are not excluded

## Reproducibility

- Data public (paper): ALMA project code given and data acknowledged via ADS/JAO  
  > "This Letter makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00532.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: clean parameters and robust value
- Missing: self-calibration details
- Missing: disk inclination and deprojection parameters
- Missing: spiral fit procedure
- Data volume (inferred): ~100-300 GB raw for four execution blocks
- Score (inferred): 3/5, Data public and processing outlined, but key imaging and modelling parameters are missing and the spiral comparison is qualitative.
- Rediscovery candidate: no, Main results are qualitative spiral matches with few numeric outputs and incomplete recipe.

## Links

- Method: Rafikov (2002) (spiral wake prescription)
- Method: Muto et al. (2012) (spiral wake prescription)
- Companion: Phuong et al. 2020 (CO analysis giving scale height and disk structure)
- Companion: Dutrey et al. (2014) (CO(6-5) hot spot detection)

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 37,
  "rate": 0.569
 },
 "evidence_ok": true
}
```
