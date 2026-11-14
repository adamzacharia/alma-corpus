# exoALMA XXII: A Two-dimensional Atlas of Deviations from Keplerian Disks

`2026ApJ..1000L..15F` | The Astrophysical Journal Letters 2026 | first author: Fukagawa, Misato | arXiv: 2603.13015 | DOI: 10.3847/2041-8213/ae3dc2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: protoplanetary_disks
- Question: How do the 2D maps of centroid velocity, line width and peak intensity in CO deviate from smooth Keplerian disks across the 15 exoALMA disks?  
  > "We provide an overview of how the observed velocity and intensity distributions deviate from those expected for a Keplerian rotating disk" (Introduction)
- Target **15 exoALMA disks (AA Tau, CQ Tau, DM Tau, HD 135344B, HD 143006, HD 34282, J1604, J1615, J1842, J1852, LkCa 15, MWC 758, PDS 66, SY Cha, V4046 Sgr)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2021.1.01123.L
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.15'' baseline (0.30'' used for some targets/species)  
  > "images with beam sizes of $0.15\ensuremath{''}$ or $0.30\ensuremath{''}$ and velocity resolutions of 28 m s$^{-1}$, 100 m s$^{-1}$, or 200 m s$^{-1}$ are utilized" (2 Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=3–2 (not stated)
- Line: 13CO J=3–2 (not stated)
- Line: CS J=7–6 (not stated)
- External data: Emission-surface heights, mean z/r of 0.28 (12CO) and 0.16 (13CO)  
  > "obtaining $\langle$$z/r$$\rangle$=0.28 and 0.16 for $^{12}$CO and $^{13}$CO, respectively" (3.1 Moment Maps) [from (cite: exoALMA_surface)]
- External data: Disk gas masses from rotation curves with self-gravity  
  > "disk masses estimated by (cite: exoALMA_rotation_curve) for 10 exoALMA sources from the rotation curves with gas self-gravity taken into account" (3.4 Overview of the Results) [from (cite: exoALMA_rotation_curve)]

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
- final beam: 0.15'' or 0.30''; channel widths 28, 100 or 200 m/s  
  > "While a synthesized beam size of $0.15\ensuremath{''}$ and a velocity resolution of 100 m s$^{-1}$ are used as the baseline" (2 Observations and Data Reduction)
- final rms: _not stated_

### Inherited from earlier work

- Calibration and imaging  
  > "The data were calibrated and imaged as detailed in (cite: exoALMA_calimg)." (2 Observations and Data Reduction) [from (cite: exoALMA_calimg)]
- Moment maps, residuals and DISCMINER modelling, including kernels and best-fit parameters  
  > "following the analysis method presented in (cite: exoALMA_discminer)" (2 Observations and Data Reduction) [from (cite: exoALMA_discminer)]

### Not stated but needed to reproduce (our reading)

- Best-fit DISCMINER parameters and kernel for each source (only in Izquierdo et al. 2025)
- Image cubes and cleaning parameters
- Masking radii used in DISCMINER fitting
- Residual-map colour scales and detection criteria for substructures

## Analysis recipe

1. **Extract moment maps**: Line-profile fitting with the best-performing kernel per source and species (Gaussian, bell, double-bell, double-Gaussian)  
  > "single-component (Gaussian, bell) and double-component (double-bell, double-Gaussian) fitting kernels were all tested and the one that best reproduced the observed spectral profiles was selected" (2 Observations and Data Reduction)
   - software: DISCMINER
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit smooth Keplerian model and make residuals**: Parametric Keplerian disk model fitted to channel maps and subtracted from the observed maps  
  > "Residual maps were created by subtracting the model disk obtained from spectral fitting using DISCMINER" (3.2 Residuals of the Centroid Velocity)
   - software: DISCMINER
   - fitting: _not stated_
   - validation: _not stated_
3. **Classify residual morphologies**: Visual classification of velocity residuals into spiral, arc/ring and other, then comparison with line-width and peak-intensity residuals  
  > "we roughly classify the sources into three categories according to the spatial distribution of the residuals: (1) spiral, (2) arc- or ring-like, and (3) other types" (3.2 Residuals of the Centroid Velocity)
   - parameter: Region within ~0.3'' excluded from discussion  
  > "We also do not discuss the inner region within approximately $0.3\ensuremath{''}$" (3.2 Residuals of the Centroid Velocity)
   - fitting: _not stated_
   - validation: 13CO maps used to support the reliability of features seen in 12CO  
  > "can therefore be used to support the reliability of the features seen in $^{12}$CO" (2 Observations and Data Reduction)

## Software

- **DISCMINER** : Moment-map extraction by line-profile fitting and Keplerian disk model fitting  
  > "The extraction of moment maps and the fitting of a smooth Keplerian disk to the data from the observations were performed using DISCMINER" (2 Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean z/r (12CO), from exoALMA_surface | 0.28 | not stated | dimensionless | 0 | obtaining $\langle$$z/r$$\rangle$=0.28 and 0.16 for $^{12}$CO and $^{13}$CO, respectively |

## Qualitative findings

- All 15 targets show large-scale deviations from smooth Keplerian disks.  
  > "We find that all targets exhibit large-scale deviations from smooth Keplerian disks" (abstract)
- Spiral arms are detected or suggested in CQ Tau, MWC 758, HD 135344B, HD 34282 and SY Cha.  
  > "Non-axisymmetric spiral-arm features are detected or suggested in five disks (CQ Tau, MWC 758, HD 135344B, HD 34282, and SY Cha)" (abstract)

## Claim tuples

- H: Do large protoplanetary disks have kinematic deviations from Keplerian rotation? | E: 2D residual maps of velocity, line width and peak intensity from DISCMINER for 15 disks | R: All disks show deviations | F: Kinematic substructures are ubiquitous in large disks | **supported**
- H: Are spirals preferentially found in Herbig Ae/Fe disks? | E: Visual classification of residual morphologies | R: Spirals in five disks, mostly Herbig | F: Spirals preferentially in Herbig Ae/Fe systems | **supported**
- H: Are some disks dynamically quiet? | E: Comparison of residuals across the three observables | R: J1852, PDS 66 and V4046 Sgr lack prominent substructures | F: They appear dynamically quieter | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Quadrupole residuals may result from a mismatch in emitting-surface height rather than dynamics.  
  > "non-Keplerian features symmetric with respect to the disk minor axis may originate from a mismatch between the actual emitting surface of the disk and the fitted smooth disk model" (3.2.4 Other Features: Quadrupole Pattern)
- How they decided it was enough: _not stated_
- Limitation (authors): Sample is biased toward large disks and not representative.  
  > "the sample is biased toward large ($>$1$\ensuremath{''}$) disks and is not representative of the full disk population" (4 Summary)
- Caveat (inferred, ours): Classification is visual and qualitative, with no quantitative detection thresholds
- Caveat (inferred, ours): Residuals depend on the smooth-model fit and can reflect surface-height or geometry mismatch
- Caveat (inferred, ours): Sample of 15 limits the Herbig vs T Tauri comparison

## Reproducibility

- Data public (paper): Line cubes and residual images are available on the exoALMA website  
  > "The data underlying this study, including the generated line cubes and residual images, are made available at: https://www.exoalma.com/home" (2 Observations and Data Reduction)
- Products in archive: _not stated_
- Code: DISCMINER is public on GitHub  
  > "https://github.com/andizq/discminer" (Footnote 1)
- Missing: Fit parameters from the DISCMINER paper
- Missing: Calibration and imaging details from the companion papers
- Data volume (inferred): Large Program of 15 disks; hundreds of GB for raw data, with released cubes smaller
- Score (inferred): 4/5, The paper is a qualitative atlas that relies on companion papers for the processing, but it uses public products and a public code.
- Rediscovery candidate: no, Results are qualitative morphological classifications and depend on companion-paper recipes.

## Links

- Method: (cite: exoALMA_discminer) (DISCMINER modelling and best-fit parameters)
- Method: (cite: exoALMA_calimg) (Calibration and imaging)
- Method: (cite: Izquierdo2021) (DISCMINER code)
- Companion: (cite: exoALMA_surface) (Emission surfaces and temperatures)
- Companion: (cite: exoALMA_pressure) (Pressure gradients)
- Companion: (cite: exoALMA_vcoherent) (Folding analysis and vertical motions)
- Related: exoALMA

## Checks

```json
{
 "quotes": 28,
 "quotes_ok": 28,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 1,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 19,
  "rate": 0.302
 },
 "evidence_ok": true
}
```
