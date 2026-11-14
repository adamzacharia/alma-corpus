# The structure of a recent nova shell as observed by ALMA

`2018MNRAS.480L..54D` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Diaz, Marcos P. | arXiv: 1808.01848 | DOI: 10.1093/mnrasl/sly121

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: stellar_physics, milky_way_ism
- Question: What is the small-scale structure of the ionised ejecta of the recent nova V5668 Sgr at mm wavelengths?  
  > "show a highly structured ionised gas distribution with small (10 [15] cm)" (abstract)
- Target **Nova V5668 Sgr (Nova Sgr 2015b)**: coordinates _not stated_; z/distance 1540 pc  
  > "A distance of 1540 pc is assumed in the present work (Banerjee et al. 2016)" (3 RESULTS); distance from Banerjee et al. 2016  
  > "A distance of 1540 pc is assumed in the present work (Banerjee et al. 2016)" (3 RESULTS)

## Data provenance

- ALMA projects: 2016.1.00682.S
- bands: Band 6 (215.4 - 232.8 GHz)  
  > "The ALMA observations of V5668 Sgr were made in band 6 (215.4 - 232.8 GHz) during cycle 4" (2 OBSERVATIONS)
- frequencies and spectral setup: Three 2 GHz continuum windows at 229.2, 219.0, 216.5 GHz; fourth window at 231.9 GHz (H30α), 1.875 GHz, 3840 channels, 0.63 km/s  
  > "Three 2 GHz spectral windows, centred at 229.2, 219.0 and 216.5 GHz, were used for continuum observation" (2 OBSERVATIONS); "The latter has a 1.875 GHz band width divided in 3840 channels, providing a resolution of 0.63 km s [−][1] ." (2 OBSERVATIONS)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 60 m to 12.7 km, 42 antennas (C40-9)  
  > "A total of 42 antennas were employed with baselines ranging from 60 m to 12.7 km" (2 OBSERVATIONS)
- angular resolution: 31 × 26 mas (Briggs); 60 × 40 mas (natural)  
  > "recovering a beam size of 31 × 26 mas at PA = 75 [◦]" (2 OBSERVATIONS)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 34 min on target (70 min total)  
  > "lasted 70 min with a 34-min exposure on target" (2 OBSERVATIONS)
- observing dates: 2017 September 28.0 UT  
  > "in 2017, September 28.0 UT" (2 OBSERVATIONS)
- pi or archival as stated: _not stated_
- Line: H H30α recombination line (231.9 GHz)
- Other facility **HST**: Hα PSF used to set convolution kernel for comparison image  
  > "aimed to match the Hubble Space Telescope (HST) Point Spread Function (PSF) at Hα" (3 RESULTS)
- External data: Distance of 1540 pc  
  > "A distance of 1540 pc is assumed in the present work (Banerjee et al. 2016)" (3 RESULTS) [from Banerjee et al. 2016]
- External data: Detailed grain data for the nova used to estimate dust emission  
  > "the detailed grain data for this nova (Gehrz et al. 2018) was used" (3 RESULTS) [from Gehrz et al. 2018]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: not possible due to weak source  
  > "Due to the weakness of the source, we were not able to self-calibrate in either weightings." (2 OBSERVATIONS)

### Imaging

- task: Hogbom CLEAN in CASA; Briggs and natural weighting  
  > "The Hogboom algorithm implemented in the CASA software (McMullin et al. 2007) was used to obtain the continuum image in two different ways." (2 OBSERVATIONS)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: 256 × 256 pixels, 5 mas pixel  
  > "The images were constructed on a 256 × 256 pixels grid with 5 mas pixel size" (2 OBSERVATIONS)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 31 × 26 mas PA 75° (Briggs); 60 × 40 mas PA 85° (natural)  
  > "For the natural weighting the resulting beam is of 60 × 40 mas at PA = 85 [◦]" (2 OBSERVATIONS)
- final rms: 0.021 mJy/beam (Briggs); cleaned to 0.026 mJy/beam  
  > "with a final RMS noise of 0.021 mJy beam [−][1]" (2 OBSERVATIONS)

### Not stated but needed to reproduce (our reading)

- Briggs robust value
- CASA version and calibration procedure (pipeline vs manual)
- Calibrators and flux scale
- Clean mask and threshold details
- Power spectrum method details (taper, normalisation)
- Clump identification and size measurement procedure
- Filling factor and hydrogen mass derivation details

## Analysis recipe

1. **Image continuum**: Hogbom CLEAN with Briggs and natural weighting  
  > "First, we used it with Briggs weighting, to recover the best possible resolution; then, we applied the natural weighting" (2 OBSERVATIONS)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared natural and Briggs images; integrated fluxes differ <12%  
  > "Both weighting methods provide comparable ( _<_ 12% difference) integrated flux densities." (2 OBSERVATIONS)
2. **Power spectrum of structure**: Power spectrum of tapered circular section of image compared with noise region  
  > "The red curve was derived from a pure noise region subjected to the same procedure." (Figure 2)
   - fitting: _not stated_
   - validation: _not stated_
3. **Identify clumps and derive densities, filling factor, mass**: Contour regions above 2.5σ, measure 32 maxima; derive free-free peak densities  
  > "Regions above 2.5 σ level were contoured and 32 emission maximums within those regions were identified and measured." (3 RESULTS)
   - assumption: Ne/NH = 2, Te = 8000 K, d = 1540 pc  
  > "assuming N e /N H = 2 and a temperature T e = 8000 K" (3 RESULTS)
   - fitting: _not stated_
   - validation: Flux–size correlation R = 0.6 suggests optically thin free-free  
  > "The flux density at these maximums correlate (R = 0.6) with the size of its corresponding condensation" (3 RESULTS)

## Software

- **CASA** : Continuum and line imaging  
  > "The Hogboom algorithm implemented in the CASA software (McMullin et al. 2007)" (2 OBSERVATIONS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total shell flux density at 230 GHz | 9.4 | 1.5 | mJy | 1 | The total measured shell flux density is 9.4 ± 1.5 mJy. |
| Peak clump electron density | ~7×10^5 | not stated | cm^-3 | 3 | has a single maximum at N e ∼ 7×10 [5] cm [−][3] |
| Filling factor upper limit | <0.2 | not stated | dimensionless | 3 | A constraint to the overall shell filling factor _f_ < 0.2 may be derived |
| Ionised hydrogen mass in clumps | ~7×10^-6 | not stated | Msun | 3 | The hydrogen mass depleted in the ionised clumps is estimated as ∼7×10 [−][6] M ⊙ . |
| Dust emission upper limit at 230 GHz | <0.2 (<3% of flux) | not stated | mJy | 3 | An upper limit to the dust emission of <0.2 mJy at 230 GHz was found |
| H30α line rms per channel | 0.1 | not stated | mJy/beam | 1 | We were able to clean each velocity channel to 0.1 mJy beam [−][1] (RMS) |

## Qualitative findings

- Large-scale structures in nova shells may result from blends of unresolved bright condensations; no extended emission above 2.5σ.  
  > "large scale structures previously distinguished in other recent nova shells may result from the distribution of bright unresolved condensations." (abstract)

## Claim tuples

- H: Is the young nova shell clumpy on small scales? | E: High-resolution Band 6 continuum imaging and power spectrum | R: Clumps down to ~1×10^15 cm; no contiguous emission above 2.5σ | F: Smallest structures seen in a nova remnant; shell is highly clumpy | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Source too weak for self-calibration; H30α not detected.  
  > "The H30α recombination line was not detected in the data cube, using either Briggs or natural weighting." (2 OBSERVATIONS)
- Caveat (inferred, ours): Clump identification at 2.5σ with rms 0.021 mJy/beam is near the noise level
- Caveat (inferred, ours): Fixed Te and distance drive density and mass
- Caveat (inferred, ours): Flux–size correlation R=0.6 is modest evidence

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration details
- Missing: Briggs robust
- Missing: Clump catalogue only on request
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 3/5, Single public dataset with basic imaging described, but many parameters and derivation details are missing.
- Rediscovery candidate: no, Recipe is incomplete for the clump density and mass derivations.

## Links

- Companion: Gehrz et al. 2018 (Grain data for V5668 Sgr and multiwavelength review)

## Checks

```json
{
 "quotes": 37,
 "quotes_ok": 37,
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
  "facts": 59,
  "stated": 26,
  "rate": 0.441
 },
 "evidence_ok": true
}
```
