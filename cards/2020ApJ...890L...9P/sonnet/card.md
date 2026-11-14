# Nine Localized Deviations from Keplerian Rotation in the DSHARP Circumstellar Disks: Kinematic Evidence for Protoplanets Carving the Gaps

`2020ApJ...890L...9P` | The Astrophysical Journal Letters 2020 | first author: Pinte, C. | arXiv: 2001.07720 | DOI: 10.3847/2041-8213/ab6dda

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Do DSHARP disks show localised velocity kinks in 12CO channel maps indicating embedded protoplanets, and do they coincide with continuum gaps?  
  > "To answer this question, we have searched through existing ALMA archival data for kinks." (Introduction)
- Target **DSHARP disks (DoAr 25, Elias 2-27, GW Lup, HD 143006, HD 163296, IM Lup, Sz 129, WaOph 6)**: coordinates _not stated_; z/distance 101-165 pc (e.g. HD 163296: 101 ± 2 pc; HD 143006: 165 ± 5 pc)  
  > "| IM Lup | 0.70 | 69 | 14 | $<700$ | $<0.24$ | 117 | 0.13 | 1.12 | 158 $\pm$ 3 | blue-shifted near side |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00484.L
- bands: _not stated_
- frequencies and spectral setup: 12CO J=2-1; channel width 244 kHz, velocity resolution 640 m/s after Hanning smoothing  
  > "The channel width of the DSHARP data is 244 kHz. Due to Hanning smoothing, the velocity resolution is 640 m.s$^{-1}$." (Observations and imaging)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CO imaged at 0.1"  
  > "were imaged at 0.1” spatial resolution due to the low signal-to-noise ratio" (Results)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Publicly available DSHARP large program data  
  > "publicly available, science ready DSHARP $^{12}$CO J=2-1 data cubes" (Observations and imaging)
- Line: 12CO J=2-1 (not stated)
- External data: Gap radii/widths, stellar masses, distances and spiral detections for the DSHARP sample  
  > "the protoplanet would also lie at the tip of a spiral arm detected in the dust continuum emission (cite: Huang2018b)" (Results) [from Huang2018b; Andrews2018b]
- External data: HD 163296 disk model with a 3 MJup planet at 260 au used for synthetic models  
  > "We used the disk model presented in (cite: Pinte2018b) for HD 163296, with a 3 M$_\mathrm{Jup}$ planet at 260 au." (Discussion) [from Pinte2018b]
- Simulation/model as data: SPH simulation (phantom) plus radiative transfer (mcfost) of a 3 MJup planet at 260 au in HD 163296 disk, at various planet azimuths  
  > "implemented by rotating each particle in the smoothed particle hydrodynamics simulation by a random angle in the disk plane prior to performing the radiative transfer" (Discussion)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Released calibrated visibilities and scripts used  
  > "we used the released non-continuum-subtracted visibilities, and adapted the released scripts to re-image with the same parameters as the fiducial" (Observations and imaging)
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
- masking: auto-masking in all cases  
  > "Here we used auto-masking in all cases" (Observations and imaging)
- multiscale scales: _not stated_
- continuum subtraction: Re-imaged without continuum subtraction and compared with subtracted cubes  
  > "we re-imaged all the CO data without continuum subtraction." (Observations and imaging)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Channel spacing 350 m/s (320 m/s for HD 163296 and HD 143006)  
  > "350 m.s$^{-1}$, except for HD 163296 and HD 143006 which were imaged with a velocity spacing of 320 m.s$^{-1}$" (Observations and imaging)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Imaging parameters of fiducial DSHARP CO images  
  > "re-image with the same parameters as the fiducial (continuum subtracted) DSHARP images (see Table 5 in (cite: Andrews2018b))" (Observations and imaging) [from Andrews2018b]
- Method for deprojecting kinks to midplane using CO emitting layer altitude  
  > "using the method described in (cite: Pinte2018a) to measure the CO emitting layer altitude" (Results) [from Pinte2018a]

### Not stated but needed to reproduce (our reading)

- Robust, taper, clean threshold and scales of the re-imaging (only in Andrews2018b Table 5)
- Exact quantitative procedure for deprojection and emitting-layer heights per disk
- Inclination, PA and systemic velocity per disk for isovelocity curves
- Model parameters of the mcfost/phantom simulations
- CASA version

## Analysis recipe

1. **Re-image CO cubes without continuum subtraction**: Re-imaged released non-continuum-subtracted visibilities with DSHARP parameters and auto-masking  
  > "adapted the released scripts to re-image with the same parameters as the fiducial (continuum subtracted) DSHARP images" (Observations and imaging)
   - software: CASA
   - fitting: _not stated_
   - validation: Kinks must appear in both subtracted and non-subtracted cubes  
  > "The kinks we present below are detected in both the continuum subtracted and non-continuum subtracted cubes in each case." (Observations and imaging)
2. **Identify velocity kinks**: Visual inspection of channel maps with isovelocity curves at ±0.2 vKep  
  > "The kinks were identified by visual inspection of the CO cubes." (Results)
   - fitting: _not stated_
   - validation: Opposite-velocity channel checked to show non-axisymmetry  
  > "demonstrating that the kink is not an axisymmetric feature" (Results)
3. **Deproject kink to planet location**: Deprojection to midplane using CO emitting layer altitude, blind to continuum gaps  
  > "this deprojection was performed blind in the continuum subtracted channel maps, i.e. without reference to the dust gap locations" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_
4. **Imaging robustness tests**: Deeper CLEAN, different uv taper, robust, scales, velocity binning, half-channel offset, beam-area-matched clean model  
  > "We also imaged the cubes with deeper CLEANing, as well as different choices of *uv* taper, robust parameters, CLEANing scales and velocity binning." (Discussion)
   - software: CASA
   - fitting: _not stated_
   - validation: Kinks remain detected in all tests  
  > "In all cases, the velocity kink remains detected." (Imaging tests)
5. **Synthetic kink detectability vs planet azimuth**: SPH + radiative transfer models, moment 1 minus azimuthally averaged model  
  > "we computed the moment 1 map and subtracted an azimuthally averaged model" (Discussion)
   - software: phantom, mcfost
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Re-imaging of CO cubes  
  > "CASA (cite: McMullin07), phantom (cite: Price2018), mcfost (cite: Pinte06; Pinte09)." (Software)
- **phantom** : SPH simulation of planet-disk  
  > "CASA (cite: McMullin07), phantom (cite: Price2018), mcfost (cite: Pinte06; Pinte09)." (Software)
- **mcfost** : Radiative transfer for synthetic channel maps  
  > "CASA (cite: McMullin07), phantom (cite: Price2018), mcfost (cite: Pinte06; Pinte09)." (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of kinks detected | 9 kinks in 8 of 18 disks | not stated | dimensionless | 2 | We detect 9 velocity kinks in 8 of 18 selected DSHARP objects. |
| Velocity deviation relative to local Keplerian | 10-15% | not stated | percent | 2 | we estimate the observed perturbations to be of order 10-15% of the local Keplerian velocity |
| Maximal Doppler flip amplitude in synthetic models | about 150 | not stated | m/s | 5 | the amplitude is small, with maximal deviations of about 150 m/s |

## Qualitative findings

- All deprojected candidate planets lie in continuum gaps; two (IM Lup, WaOph 6) also at spiral tips  
  > "In every case the candidate protoplanet would lie within a gap in the dust continuum emission." (Results)

## Claim tuples

- H: Do DSHARP disks show planet-induced velocity kinks? | E: Visual search of 12CO cubes, with and without continuum subtraction | R: 9 kinks in 8 of 18 disks | F: Candidate protoplanets, requiring confirmation | **partially**
- H: Are kinks associated with dust gaps? | E: Deprojection of kinks to disk midplane | R: All lie in a gap and/or at a spiral end | F: Many dust gaps likely carved by protoplanets | **supported**
- H: Are kinks imaging artefacts? | E: Re-imaging variants and no continuum subtraction | R: Kinks persist | F: Not artefacts of tested imaging choices | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Continuum subtraction, optical depth/emitting layer gaps, massive companions, pressure gradients considered as alternatives  
  > "Several observational effects and physical mechanisms may produce features in the channel maps that look like velocity kinks." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): No quantitative detection confidence; limited S/N and spectral resolution; cloud contamination  
  > "There is currently no quantitative means of assessing confidence in a detection" (Results)
- Caveat (inferred, ours): Detection by visual inspection is subjective and without false-positive estimate
- Caveat (inferred, ours): Single-channel detections at S/N ~7-14 may be noise or cloud structure
- Caveat (inferred, ours): Gap association could be partly coincidence given many gaps per disk

## Reproducibility

- Data public (paper): Public DSHARP data and scripts  
  > "publicly available, science ready DSHARP $^{12}$CO J=2-1 data cubes" (Observations and imaging)
- Products in archive: _not stated_
- Missing: Imaging parameters only by reference to Andrews2018b
- Missing: No objective kink-detection criterion
- Missing: Deprojection details by reference
- Data volume (inferred): tens to ~100 GB for 18 disks' CO visibilities/cubes
- Score (inferred): 3/5, Public data and scripts, but detection is visual and key parameters are inherited.
- Rediscovery candidate: no, Main results are qualitative visual detections, not numeric.

## Links

- Method: Pinte2018a (Emitting layer altitude / deprojection method)
- Method: Pinte2018b (Kink technique and HD 163296 model)
- Companion: Andrews2018b (DSHARP overview and imaging parameters)
- Companion: Perez_DSHARP (HD 143006 kink)
- Related: DSHARP

## Checks

```json
{
 "quotes": 38,
 "quotes_ok": 38,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 29,
  "rate": 0.42
 },
 "evidence_ok": true
}
```
