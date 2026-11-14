# H<SUB>2</SUB>CO Distribution and Formation in the TW HYA Disk

`2017ApJ...839...43O` | The Astrophysical Journal 2017 | first author: Öberg, Karin I. | arXiv: 1704.05133 | DOI: 10.3847/1538-4357/aa689a

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What is the radial and vertical H2CO distribution in the TW Hya disk, and does it indicate gas-phase and/or grain-surface formation?  
  > "Yet its distribution and dominant formation pathway(s) remain largely unconstrained." (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance 59 pc  
  > "Because TW Hya is nearby (d=59 pc (Gaia Collaboration et al. 2016))" (1. INTRODUCTION); distance from Gaia Collaboration et al. 2016  
  > "Because TW Hya is nearby (d=59 pc (Gaia Collaboration et al. 2016))" (1. INTRODUCTION)

## Data provenance

- ALMA projects: 2013.1.00114.S, 2013.1.00198.S
- bands: _not stated_
- frequencies and spectral setup: Channel width 122 kHz (~0.16 km/s) for 3_12-2_11; 244 kHz (0.21 km/s) for 5_15-4_14; imaged at 0.25 km/s  
  > "The H 2 CO 5 15 _−_ 4 14 transition was observed using a channel width of 244kHz" (2.1 Observational Details)
- continuum bandwidth: 469 MHz line-free spectral window for continuum  
  > "We used a separate line-free spectral window with a frequency width of 469 MHz to" (2.1 Observational Details)
- arrays: 31 antennas (3_12-2_11); 34 and 36 antennas (5_15-4_14)  
  > "with 31 antennas and baselines ranging from 30 to 650 m." (2.1 Observational Details)
- configurations: _not stated_
- baselines: 30-650 m (3_12-2_11); 15-349 m and 21-784 m (5_15-4_14)  
  > "with 31 antennas and baselines ranging from 30 to 650 m." (2.1 Observational Details)
- angular resolution: 0.45"x0.45" and 0.47"x0.41"  
  > "0 _[′′]_ _._ 45 _×_ 0 _[′′]_ _._ 45 ( _−_ 75 _[◦]_ )" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 41 min (3_12-2_11); 43 min (5_15-4_14)  
  > "The total on-source integration time was 41 minutes." (2.1 Observational Details)
- observing dates: 2014 July 19; 2014 December 31 and 2015 June 15  
  > "H 2 CO 5 15 _−_ 4 14 was observed on December 31, 2014 and" (2.1 Observational Details)
- pi or archival as stated: 3_12-2_11 PI K. Oberg; 5_15-4_14 PI E. Bergin  
  > "ADS/JAO.ALMA#2013.1.00198.S (PI: E. Bergin)" (2.1 Observational Details)
- Line: H2CO 3_12-2_11 (225.69778 GHz)
- Line: H2CO 5_15-4_14 (351.76864 GHz)
- External data: TW Hya disk density and temperature model fit to SED and continuum  
  > "developed to fit the TW Hya SED and the disk continuum emission (Qi et al. 2013a)" (3. H 2 CO TOY MODELS) [from Qi et al. 2013a (cite: Qi et al. 2013a)]
- External data: Previous SMA continuum flux 540 mJy  
  > "previously measured flux of 540 mJy with the Submillimeter Array" (2.1 Observational Details) [from Qi et al. 2006]
- External data: Systemic velocity of TW Hya  
  > "close to the previously observed systemic velocity of TW Hya (Hughes et al. 2011)" (2.2 H 2 CO Spectral Image Cubes) [from Hughes et al. 2011]

## Processing

### Calibration

- pipeline or manual: JAO pipeline-calibrated data, then phase and amplitude self-calibration on continuum  
  > "the pipeline-calibrated data from JAO were phase and amplitude self calibrated" (2.1 Observational Details)
- casa version: CASA 4.5  
  > "CASA version 4.5 and timescales of 10–30 seconds" (2.1 Observational Details)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pallas (July 2014); Titan (5_15-4_14)  
  > "Pallas for flux calibration." (2.1 Observational Details)
- flux scale uncertainty: 15%  
  > "assuming a 15% absolute flux calibration uncertainty" (2.1 Observational Details)
- self calibration: phase and amplitude on continuum, 10-30 s; SNR increased by ~3  
  > "This increased the SNR of the emission by a factor of _≈_ 3." (2.1 Observational Details)

### Imaging

- task: _not stated_
- deconvolver: Hogbom CLEAN to 3x rms  
  > "down to a level of 3 _×_ rms." (2.1 Observational Details)
- weighting robust: Briggs parameter 0.5  
  > "and Briggs parameter of 0.5." (2.1 Observational Details)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: manually identified emission per channel  
  > "a mask, constructed by manually identifying areas with emission in each channel" (2.1 Observational Details)
- multiscale scales: _not stated_
- continuum subtraction: line data continuum subtracted  
  > "The line data were continuum subtracted and imaged." (2.1 Observational Details)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.45"x0.45" and 0.47"x0.41"  
  > "0 _[′′]_ _._ 47 _×_ 0 _[′′]_ _._ 41 (51 _[◦]_ )" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Phase-center alignment of compact and extended data using continuum peak  
  > "we aligned phase-centers of the compact and extended data sets based on the continuum peak location" (2.1 Observational Details) [from Bergin et al. 2016]
- Disk physical model (density/temperature)  
  > "Qi et al. (2013a) explored several different vertical dust grain distributions," (3. H 2 CO TOY MODELS) [from Qi et al. 2013a]

### Not stated but needed to reproduce (our reading)

- CLEAN masks per channel
- Self-calibration solution intervals per dataset and reference antenna details
- Image size and cell size
- Line-free channels used for continuum subtraction
- Disk position angle and stellar mass for the model
- Exact model grid and by-eye fit criteria

## Analysis recipe

1. **Image line cubes and continuum**: Self-calibrate, continuum-subtract, CLEAN with mask  
  > "The line data were continuum subtracted and imaged." (2.1 Observational Details)
   - software: CASA
   - parameter: Briggs 0.5, 0.25 km/s channels, 3 rms threshold  
  > "We CLEANed (H¨ogbom 1974) the images with a 0.25" (2.1 Observational Details)
   - fitting: _not stated_
   - validation: Continuum subtraction applied to line-free channels showed no hole  
  > "We saw no significant emission hole in the resulting image." (2.2 H 2 CO Spectral Image Cubes)
2. **Moment maps, radial profiles and spectra**: immoments without clipping; azimuthal averaging; spectra summed within CLEAN mask  
  > "The images were generated in CASA using the _immoments_ task without clipping" (2.2 H 2 CO Spectral Image Cubes)
   - software: CASA
   - parameter: inclination 7 degrees  
  > "azimuthally averaged radial profiles assuming an inclination of 7 degrees" (2.2 H 2 CO Spectral Image Cubes)
   - fitting: _not stated_
   - validation: _not stated_
3. **Toy abundance models compared with observed profiles**: Parametric H2CO abundance in fixed disk model, LTE level populations, visibility sampling, by-eye comparison of radial profiles  
  > "assuming the gas is at local thermal equilibrium (LTE)" (3. H 2 CO TOY MODELS)
   - software: RADMC-3D, vis_sample
   - parameter: (z/r)up=0.3, rout=100 AU fixed; vary inner radius, lower boundary, power law  
  > "We fix the upper ( _z/r_ ) up and outer ( _r_ out ) boundaries to 0.3 and 100 AU, respectively." (3.1 Single component models)
   - assumption: LTE justified by densities above 1e6 cm-3  
  > "typical disk densities are above 1 _×_ 10 [6] cm _[−]_ [3], justifying our assumption" (3. H 2 CO TOY MODELS)
   - fitting: by-eye fit, no sampler  
  > "to obtain a reasonable ‘by-eye’ fit to the H 2 CO 3 12 _−_ 2 11 emission." (3.1 Single component models)
   - validation: Channel-map residuals >5 sigma remain  
  > "there are significant residuals ( _>_ 5 _σ_ )." (3.3 Model comparison)

## Software

- **CASA** 4.5: self-calibration, CLEAN imaging, immoments  
  > "CASA version 4.5 and timescales of 10–30 seconds" (2.1 Observational Details)
- **RADMC-3D** 0.39: level populations and emission under LTE  
  > "computed using RADMC-3D version 0.39 (Dullemond 2012)" (3. H 2 CO TOY MODELS)
- **vis_sample** : Fourier transform and sampling of model visibilities  
  > "to compute the Fourier Transform of the synthetic model and sample visibilities" (3. H 2 CO TOY MODELS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total 1.3 mm continuum flux | 560 | 84 mJy (15% abs. calibration) | mJy | 1 | The total continuum flux is 560 _±_ 84 mJy |
| H2CO 3_12-2_11 peak integrated flux | 26.7 | 2.5 | mJy km/s beam-1 | 2 | 26.7 _±_ 2.5 52.8 _±_ 2.9 |
| H2CO 5_15-4_14 peak integrated flux | 57.0 | 3.9 | mJy km/s beam-1 | 2 | 57.0 _±_ 3.9 96.3 _±_ 3.8 |
| Radial emission bump location | 1.05 arcsec (62 au) | not stated | arcsec | 2 | a ‘bump’ around 1 _[′′]_ _._ 05 (62 au) |

## Qualitative findings

- Both lines show central depression, with 3_12-2_11 deeper; no single-component model fits both lines  
  > "A single-component parametric model appears to be ruled out by the data." (3.1 Single component models)

## Claim tuples

- H: Does H2CO in TW Hya require more than one component? | E: Toy abundance models compared with radial profiles of two lines | R: Single power-law models fail; inner hot unresolved component plus outer component needed | F: At least two H2CO reservoirs: warm inner (<10 au) and outer from ~15 au | **supported**
- H: Does the line ratio constrain the outer emitting layer? | E: Flared and 3-component models | R: High 5_15-4_14/3_12-2_11 ratio in outer disk | F: Outer emission arises in a more elevated or warmer layer | **partially**
- H: Is grain-surface formation active in the TW Hya disk? | E: Compare inferred abundance structure with chemistry models | R: Qualitative agreement | F: Active grain-surface chemistry is implied | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Exploratory phase, so toy models instead of grid or MCMC that assume the correct model form  
  > "Since we are in an exploratory" (3. H 2 CO TOY MODELS)
- Alternative: Continuum over-subtraction, line opacity and dust opacity ruled out as causes of central depression  
  > "we have to exclude three other potential sources: continuum over-subtraction, line opacity, and dust opacity." (2.2 H 2 CO Spectral Image Cubes)
- How they decided it was enough: _not stated_
- Limitation (authors): Disk vertical temperature structure highly uncertain; abundances not accurate; toy models leave >5 sigma residuals  
  > "it is difficult to constrain the vertical emission layer of molecules in absolute terms, or derive accurate H 2 CO abundances." (3. H 2 CO TOY MODELS)
- Caveat (inferred, ours): By-eye fits without uncertainties; degeneracy between layer height and temperature
- Caveat (inferred, ours): Model fixed to pre-Gaia distance
- Caveat (inferred, ours): No formal fitting or error bars on model parameters

## Reproducibility

- Data public (paper): Data identified by ALMA project codes  
  > "ADS/JAO.ALMA#2013.1.00114.S (PI: K. Oberg)" (2.1 Observational Details)
- Products in archive: _not stated_
- Code: vis_sample publicly available on GitHub  
  > "package is publicly available at" (3. H 2 CO TOY MODELS)
- Missing: Disk model files from Qi et al. 2013a
- Missing: CLEAN masks and imaging grid parameters
- Missing: By-eye fit criteria
- Data volume (inferred): ~50-100 GB for three execution blocks
- Score (inferred): 3/5, Data identified and model parameters tabulated, but by-eye fitting and missing imaging details limit exact reproduction.
- Rediscovery candidate: no, Main results are qualitative model comparisons by eye rather than numeric.

## Links

- Method: Qi et al. 2013a (Source of the TW Hya disk physical model)
- Companion: Loomis et al. 2015 (H2CO in the DM Tau disk)
- Companion: Bergin et al. 2016 (Same 5_15-4_14 dataset and alignment)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 45,
  "rate": 0.662
 },
 "evidence_ok": true
}
```
