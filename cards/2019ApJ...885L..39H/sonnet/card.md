# First Detection of Submillimeter-wave [<SUP>13</SUP>C I] <SUP>3</SUP> P <SUB>1</SUB>-<SUP>3</SUP> P <SUB>0</SUB> Emission in a Gaseous Debris Disk of 49 Ceti with ALMA

`2019ApJ...885L..39H` | The Astrophysical Journal Letters 2019 | first author: Higuchi, Aya E. | arXiv: 1909.09748 | DOI: 10.3847/2041-8213/ab518d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: debris_disks, astrochemistry
- Question: Can the [13C I] 3P1-3P0 F=3/2-1/2 hyperfine line be detected in the 49 Ceti gas disk, and what does the [C I]/[13C I] ratio imply for [C I] optical depth?  
  > "Since the [C I] emission in 49 Ceti is bright and narrow in the outer part of the disk (120 to 180 au), we carefully inspected their spectra to identify [$^{13}$C I]." (Introduction)
- Target **49 Ceti**: coordinates _not stated_; z/distance 57±0.3 pc  
  > "whose distance is 57$\pm$0.3 pc (cite: gai18)" (Introduction); distance from Gaia Collaboration 2018 (gai18)  
  > "whose distance is 57$\pm$0.3 pc (cite: gai18)" (Introduction)

## Data provenance

- ALMA projects: 2017.0.00467.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: about 0.5 arcsec  
  > "averaged over the 0.$\ensuremath{''}$5 areas in diameter which correspond to the spatial resolution" (Detection of [13C I] 3P1-3P0 line emission)
- max recoverable scale: _not stated_
- sensitivity: rms 0.11 K at 0.1 km/s resolution; 1 sigma = 5.5 mJy/beam in P-V diagram  
  > "the root-mean-square (rms) noise level of the spectra is 0.11 K at a resolution of 0.1 km s$^{-1}$" (Detection of [13C I] 3P1-3P0 line emission); "1$\sigma$ = 5.5 mJy beam$^{-1}$" ([C I] 3P1-3P0 line emission)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [C I] 3P1-3P0 (492.160651 GHz)
- Line: [13C I] 3P1-3P0 F=3/2-1/2 (492.164276 GHz)
- Line: [13C I] 3P1-3P0 F=1/2-1/2 (492.160147 GHz)
- External data: Laboratory rest frequencies of [C I] and [13C I] lines  
  > "were precisely measured by the laboratory microwave spectroscopy (cite: yam91)" (Introduction) [from (cite: yam91)]
- External data: ISM 12C/13C abundance ratio of 77  
  > "the $^{12}$C/$^{13}$C abundance ratio is that of the interstellar medium (77) (cite: wil94)" ([C I] 3P1-3P0 line emission) [from (cite: wil94)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs weighting, robust = +0.5  
  > "Briggs weighting of +0.5 was used to obtain the spectra (cite: pet12)." (Dataset)
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

- Observation details (weather, calibrators, resolutions, data quality) reported in earlier paper  
  > "Details of the [C I] observations (weather condition, calibrators, spatial and velocity resolutions, and data qualities) have already been reported by (cite: hig19)." (Dataset) [from (cite: hig19)]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging details (cell size, image size, deconvolver, masking, continuum subtraction, line-free channels)
- Exact positions of the six spectral extraction circles
- Array configuration, spectral setup and on-source time
- How the 12±3 ratio and its uncertainty were computed
- RADEX line width/collision data and optimization method

## Analysis recipe

1. **Image the [C I] cube**: Reduced with CASA 5.5.0, Briggs weighting +0.5  
  > "Data reduction was performed by using version 5.5.0 of the Common Astronomy Software Applications (CASA) package (cite: mcm07)." (Dataset)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract spectra at six positions and identify [13C I]**: Spectra averaged over 0.5 arcsec circles; compare with [C I] spectrum scaled by 1/12 and shifted by -2.2 km/s  
  > "The overlaid spectra with pink color show the [C I] spectra whose intensity is scaled by 1/12 and whose velocity is blue-shifted by 2.2 km s$~^{-1}$" (Detection of [13C I] 3P1-3P0 line emission)
   - software: CASA
   - fitting: _not stated_
   - validation: Visual match of scaled [C I] spectrum to faint feature  
  > "The overlaid spectra well correspond to the faint features." (Detection of [13C I] 3P1-3P0 line emission)
3. **Derive optical depth**: Use intensity ratio and hyperfine relative intensities  
  > "The peak optical depth ($\tau$) of the [C I] emission is roughly estimated to be 10$\pm$3 by considering the relative intensities of the hyperfine components." ([C I] and [13C I] intensity ratio)
   - assumption: 12C/13C = 77; Tex of [13C I] equals that of [C I]  
  > "Here, we assumed the excitation temperature of [$^{13}$C I] is identical to that of [C I]." ([C I] and [13C I] intensity ratio)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive N(C) and TK with non-LTE**: RADEX optimized to reproduce [C I] intensity and optical depth  
  > "We optimized these two parameters to reproduce the [C I] intensity and its optical depth (10$\pm$3) derived above." ([C I] and [13C I] intensity ratio)
   - software: RADEX
   - parameter: H2 density 10^4 cm^-3; velocity width 1 km/s  
  > "Here, the velocity width is assumed to be 1 km s$^{-1}$." ([C I] and [13C I] intensity ratio)
   - assumption: Electron collisions ignored  
  > "we ignored it for [C I] in this calculation" ([C I] and [13C I] intensity ratio)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.5.0: Data reduction, impv P-V diagram  
  > "Data reduction was performed by using version 5.5.0 of the Common Astronomy Software Applications (CASA) package (cite: mcm07)." (Dataset)
- **RADEX** : Non-LTE derivation of N(C) and TK  
  > "by using the non-LTE code (RADEX)" ([C I] and [13C I] intensity ratio)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [C I]/[13C I] intensity ratio | 12 | ±3 | dimensionless | 3 | The [C I]/[13C I] line intensity ratio is found to be 12$\pm$3 |
| [C I] peak optical depth | 10 | ±3 | dimensionless | 3 | estimated to be 10$\pm$3 |
| Kinetic temperature | 18 | ±7 | K | 4 | $T{\rm_{K}}$ = 18$\pm$7 K |
| N(C) | 1.5e18 | ±1.0e18 | cm^-2 | 4 | $N$(C) = (1.5$\pm$1.0) $\times$ 10$^{18}$ cm$^{-2}$ |

## Qualitative findings


## Claim tuples

- H: [13C I] F=3/2-1/2 is detectable in 49 Ceti outer disk | E: Spectra at six positions compared with scaled, shifted [C I] | R: Faint feature at expected velocity at 3-5 sigma in NW positions | F: First detection of [13C I] 492 GHz | **supported**
- H: [C I] is optically thick | E: Compare observed ratio to ISM 12C/13C | R: Ratio 12±3 vs 77 | F: [C I] is optically thick at least partly | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Southeast positions not definitively detected due to [C I] wing contamination; 12C/13C may exceed 77 so tau is a lower limit  
  > "we cannot detect the [$^{13}$C I] line definitively, because of the heavy contamination of the wing component" (Detection of [13C I] 3P1-3P0 line emission)
- Caveat (inferred, ours): Detection is only 3-5 sigma per position
- Caveat (inferred, ours): Assumed 12C/13C=77 and equal Tex
- Caveat (inferred, ours): RADEX assumed H2 density arbitrary

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Full calibration/imaging parameters
- Missing: Spectral extraction positions
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Simple analysis on public data but imaging and extraction details are sparse and deferred to a companion paper.
- Rediscovery candidate: no, Recipe is incomplete and the detection is marginal.

## Links

- Companion: (cite: hig19) (Original [C I] observations and imaging of 49 Ceti)

## Checks

```json
{
 "quotes": 32,
 "quotes_ok": 32,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2017.0.00467.S"
 ],
 "obscore_codes_not_in_card": [
  "2017.1.00467.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 20,
  "rate": 0.312
 },
 "evidence_ok": true
}
```
