# ALMA observations of the variable <SUP>12</SUP>CO/<SUP>13</SUP>CO ratio around the asymptotic giant branch star R Sculptoris

`2013A&A...556L...1V` | Astronomy and Astrophysics 2013 | first author: Vlemmings, W. H. T. | arXiv: 1308.3703 | DOI: 10.1051/0004-6361/201321821

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: Does the 12CO/13CO ratio vary spatially in the circumstellar envelope of R Scl (detached shell vs present-day mass loss), and what does this imply for the 12C/13C ratio?  
  > "The effect of, for example, an inhomogeneous circumstellar environment or (hidden) companion on the $^{12}$CO/$^{13}$CO ratio throughout the circumstellar envelope is thus poorly known." (Introduction)
- Target **R Sculptoris (R Scl)**: coordinates RA(J2000) 01h26m58.094s, Dec -32d32m35.454s (mosaic center)  
  > "the carbon-rich AGB star R Scl located at $\sim290$ pc (cite: Knapp03)" (Introduction); "The center pointing of the mosaic was taken to be the position of R Scl at $\alpha(J2000) = {01}^{\rm h}{26}^{\rm m}{58}s{094}$" (ALMA observations and results); z/distance ~290 pc  
  > "the carbon-rich AGB star R Scl located at $\sim290$ pc (cite: Knapp03)" (Introduction); "The center pointing of the mosaic was taken to be the position of R Scl at $\alpha(J2000) = {01}^{\rm h}{26}^{\rm m}{58}s{094}$" (ALMA observations and results); distance from Knapp et al. 2003  
  > "the carbon-rich AGB star R Scl located at $\sim290$ pc (cite: Knapp03)" (Introduction); "The center pointing of the mosaic was taken to be the position of R Scl at $\alpha(J2000) = {01}^{\rm h}{26}^{\rm m}{58}s{094}$" (ALMA observations and results)

## Data provenance

- ALMA projects: 2011.0.00131.S
- bands: Band 7 (275-373 GHz)  
  > "were observed using ALMA Band 7 (275-373 GHz) on October 3–4 and 18–19 2011 during the ALMA cycle 0 observing program" (ALMA observations and results)
- frequencies and spectral setup: four spectral windows of 1.875 GHz, 3840 channels each, tuned at 345.1, 343.3, 331.1, 333.0 GHz; 0.488 MHz channel spacing after Hanning smoothing (0.44 km/s)  
  > "The Band 7 data contained four spectral windows of 1.875 GHz and 3840 channels each that were tuned at 345.1 GHz, 343.3 GHz, 331.1 GHz, and 333.0 GHz." (ALMA observations and results); "The channel spacing of 0.488 MHz resulted after Hanning smoothing, in a maximum spectral resolution of $0.44$ km s$^{-1}$." (ALMA observations and results)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: cycle 0 compact configuration  
  > "The data were taken using the cycle 0 compact configuration of ALMA, with baselines ranging from 15 m to 200 m." (ALMA observations and results)
- baselines: 15 m to 200 m  
  > "with baselines ranging from 15 m to 200 m" (ALMA observations and results)
- angular resolution: 1.65"x1.35" at 330 GHz, PA 86 deg (natural weighting)  
  > "this resulted in a beam size of $1.65"\times1.35"$ (at 330 GHz) with a position angle of 86$^\circ$" (ALMA observations and results)
- max recoverable scale: emission at scales larger than ~15" resolved out  
  > "Emission at scales larger than $\sim15"$ is resolved out." (ALMA observations and results)
- sensitivity: rms ~15 mJy/beam (13CO) and ~25 mJy/beam (12CO) in line channels at 3 km/s  
  > "The rms in the emission line channels was $\sim15$ mJy beam$^{-1}$ and $\sim25$ mJy beam$^{-1}$ for the $^{13}$CO($J\,$=$\,$3$\,\to\,$2) and $^{12}$CO($J\,$=$\,$3$\,\to\,$2) lines, respectively." (ALMA observations and results)
- time on source: 2.42 min per mosaic pointing; ~3.8 hours total observing time  
  > "Each mosaic pointing was observed for a total of 2.42 min and the total observing time was approximately 3.8 hours." (ALMA observations and results)
- observing dates: October 3–4 and 18–19 2011  
  > "on October 3–4 and 18–19 2011 during the ALMA cycle 0 observing program" (ALMA observations and results)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (345.795 GHz)
- Line: 13CO J=3-2 (330.587 GHz)
- Other facility **APEX**: single-dish 12CO and 13CO(3-2) spectra to estimate ALMA flux loss  
  > "we compared the interferometric observations with new spectra taken with the APEX telescope." (Comparison with single dish observations)
- External data: Photospheric 12C/13C ratio of ~19  
  > "differs significantly from the value of $\sim19$ determined using molecular tracers in the stellar photosphere (cite: Lambert86)" (Discussion) [from (cite: Lambert86)]
- External data: Correlation I(12CO)/I(13CO) = (0.6±0.2) x 12C/13C  
  > "these authors determined a correlation of the form" (Discussion) [from (cite: Schoeier00)]
- External data: Present-day mass-loss density, velocity, temperature and stellar parameters  
  > "are taken to be the same as described in (cite: Schoeier05), as are the stellar parameters." (Radiative transfer modeling) [from (cite: Schoeier05)]

## Processing

### Calibration

- pipeline or manual: Manual steps in CASA (WVR correction, Tsys correction, antenna position improvement, manual delay calibration)  
  > "we improved the antenna positions and performed a manual delay calibration." (ALMA observations and results)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune, bootstrapped to gain calibrator J0137-245; bandpass on 3C454.3  
  > "The primary flux calibration was made using Neptune and bootstrapping to the gain calibrator J0137-245 ($0.49$ Jy beam$^{-1}$)." (ALMA observations and results)
- flux scale uncertainty: ~10%  
  > "the absolute flux calibration has an uncertainty of $\sim10\%$" (ALMA observations and results)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "Imaging was then done using the CASA clean algorithm" (ALMA observations and results)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Using natural weighting to optimize the sensitivity for the weak $^{13}$CO emission" (ALMA observations and results)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: smoothed to 3 km/s (same for 12CO)  
  > "smoothing the data to 3 km s$^{-1}$ to detect the weak $^{13}$CO($J\,$=$\,$3$\,\to\,$2) emission" (ALMA observations and results)
- final beam: 1.65"x1.35", PA 86 deg  
  > "beam size of $1.65"\times1.35"$ (at 330 GHz) with a position angle of 86$^\circ$" (ALMA observations and results)
- final rms: ~15 mJy/beam (13CO)  
  > "The rms in the emission line channels was $\sim15$ mJy beam$^{-1}$" (ALMA observations and results)

### Inherited from earlier work

- 12CO(3-2) observations and results from same dataset  
  > "The results of the $^{12}$CO($J\,$=$\,$3$\,\to\,$2) observations were presented in M+12" (ALMA observations and results) [from Maercker et al. 2012 (M+12)]
- Radiative transfer code  
  > "using the code described in detail in (cite: Schoeier01)" (Radiative transfer modeling) [from (cite: Schoeier01)]
- Conversion of intensity ratio to 12C/13C  
  > "we can determine the latter following (cite: Schoeier00)" (Discussion) [from (cite: Schoeier00)]

### Not stated but needed to reproduce (our reading)

- clean threshold, masking, iterations, mosaic imaging details
- cell and image size
- continuum subtraction and line-free channels
- how ratio maps were built (clipping thresholds, regridding, common beam)
- exact radiative transfer model grids and fit procedure for abundance ratio
- calibrator for phase/other details and CASA version
- APEX data reduction details and ALMA flux-loss comparison method

## Analysis recipe

1. **Calibrate and image 13CO and 12CO(3-2) cubes**: CASA calibration, then clean with natural weighting, smoothing to 3 km/s  
  > "Imaging was then done using the CASA clean algorithm, smoothing the data to 3 km s$^{-1}$ to detect the weak $^{13}$CO($J\,$=$\,$3$\,\to\,$2) emission." (ALMA observations and results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Check flux loss against single dish**: Compare ALMA spectra over APEX beam area (~19") with APEX 12CO and 13CO(3-2) spectra  
  > "We only recover approximately $25\%$ of the total flux" (Comparison with single dish observations)
   - fitting: _not stated_
   - validation: Similar ~25% recovery for both lines implies ratios unaffected  
  > "$25\%$ of the total flux is detected for both transitions, with correspondingly little effect on the observed flux ratios" (Comparison with single dish observations)
3. **Map 12CO/13CO intensity ratio and convert to 12C/13C**: Intensity ratio maps; apply I(12CO)/I(13CO) = (0.6±0.2) x 12C/13C  
  > "Applying this relation to the average ratios found in the shell and present-day mass loss" (Discussion)
   - assumption: Intensity ratio related to isotope ratio; optical depth, photodissociation and fractionation neglected  
  > "these derived ratios do not take into account optical depth effects, nor effects such as selective photo-dissociation and chemical fractionation" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_
4. **Radiative transfer modelling of abundance ratio**: Two-component model (present-day mass loss + detached shell) with code of Schoeier & Olofsson 2001; only the abundance ratio in the present-day mass loss varied  
  > "Finally, we only varied the $^{12}$CO and $^{13}$CO abundance ratio in the present-day mass loss." (Radiative transfer modeling)
   - software: Schoeier01 radiative transfer code
   - parameter: Mdot=3e-7 Msun/yr; shell width ~400 AU; shell mass 2.5e-3 Msun; shell T 50 K  
  > "For the shell, we assumed a uniform gas density with a shell width of $\sim 400$ AU and a total mass of $2.5\times10^{-3}$ M$_\odot$." (Radiative transfer modeling); "We furthermore assumed an average temperature of $50$ K for the shell." (Radiative transfer modeling)
   - assumption: Distance ~290 pc; no spiral included in model  
  > "we do not include a description of the spiral in our models because no $^{13}$CO was detected between the shell and the more recent mass loss" (Radiative transfer modeling)
   - fitting: _not stated_
   - validation: Model compared to ALMA (5") and APEX (19") spectra  
  > "A comparison of the observations with the flux of the model used to fit the $^{13}$CO data" (Comparison with single dish observations)

## Software

- **CASA** : data reduction and imaging (clean)  
  > "The data were reduced using the Common Astronomy Software Application (CASA)." (ALMA observations and results)
- **Schoeier & Olofsson 2001 radiative transfer code** : CO radiative transfer modeling  
  > "we performed radiative transfer calculations for the CO emission using the code described in detail in (cite: Schoeier01)" (Radiative transfer modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12C/13C in shell (from intensity ratio) | ~12 | not stated | dimensionless | 3 | the carbon isotope ratio of R Scl has increased from $\sim12$ when the detached shell was formed to $\sim115$ during the recent mass loss |
| 12C/13C in present-day mass loss (from intensity ratio) | ~115 | not stated | dimensionless | 3 | the carbon isotope ratio of R Scl has increased from $\sim12$ when the detached shell was formed to $\sim115$ during the recent mass loss |
| 12CO/13CO abundance ratio in present-day mass loss (model) | >60 | not stated | dimensionless | 4 | Our radiative transfer models furthermore indicate that the CO isotope ratio in the present-day mass loss is $>60$. |
| average 12CO/13CO ratio in shell (model) | 19 | not stated | dimensionless | 4 | using an *average* $^{12}$CO/$^{13}$CO ratio of $19$ in the shell |
| average intensity ratio over entire envelope | 10 | ±3 | dimensionless | 3 | we find an intensity ratio of $10\pm3$ |
| fraction of flux recovered by ALMA | ~25% | not stated | percent | 2 | We only recover approximately $25\%$ of the total flux |
| shell intensity ratio range | ~1.5 to >40 | not stated | dimensionless | 3 | the intensity ratio ranges between as low as $\sim1.5$ to $>40$ where no $^{13}$CO is detected |

## Qualitative findings

- Shell is clumpy; lowest intensity ratios anti-correlated with strongest 12CO peaks, consistent with fractionation in cold clumps  
  > "We find that the lowest $^{12}$CO/$^{13}$CO intensity ratios are found to be anti-correlated with the strongest $^{12}$CO peaks." (Isotope ratio in the detached shell)

## Claim tuples

- H: The 12CO/13CO ratio differs between the detached shell and present-day mass loss | E: Ratio maps from ALMA 12CO and 13CO(3-2) plus radiative transfer models | R: Shell ratio 19 reproduces data; present-day mass loss needs ratio >60 (at least 3x higher) | F: Ratio decreased by at least a factor of three in the shell relative to recent mass loss | **supported**
- H: Missing short spacings bias the ratio | E: Compare with APEX single-dish spectra | R: ~25% recovered for both lines | F: Conclusions on ratios are robust | **supported**
- H: Variations within the shell arise from fractionation vs photodissociation | E: Inspect ratio map vs 12CO peaks | R: Low ratios anti-correlated with 12CO peaks | F: Fractionation in clumpy cold gas likely dominates | **partially**

## Reasoning

- Why this data: ALMA gives resolution and sensitivity to map weak circumstellar 13CO, which single dishes could not  
  > "for the first time provides sufficient angular resolution and sensitivity to map the circumstellar $^{13}$CO emission of AGB stars in detail" (Introduction)
- Why this method: _not stated_
- Alternative: Third dredge-up during thermal pulse rejected as explanation for ratio increase  
  > "However, this scenario is unlikely for two main reasons" (Isotope ratio in the present-day mass loss)
- How they decided it was enough: _not stated_
- Limitation (authors): Shell temperature poorly constrained; derived ratios ignore optical depth and chemistry  
  > "the shell temperature is poorly constrained" (Radiative transfer modeling)
- Caveat (inferred, ours): Intensity-to-abundance conversion relies on a calibration from single-dish sample
- Caveat (inferred, ours): 13CO weakly detected in present-day mass loss (4 sigma) so ratio is a lower limit
- Caveat (inferred, ours): Only 25% of flux recovered; spatially varying flux loss not excluded
- Caveat (inferred, ours): UV explanation speculative

## Reproducibility

- Data public (paper): ALMA project data cited; image cubes at CDS  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00131.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: clean parameters and masks
- Missing: ratio map construction details
- Missing: radiative transfer model code/grids and fitting details
- Missing: APEX reduction
- Data volume (inferred): ~20-50 GB (Cycle 0 Band 7 mosaic, 4 spws)
- Score (inferred): 3/5, Public data and clear observing setup, but imaging and modelling details are sparse; short letter.
- Rediscovery candidate: no, Imaging and radiative transfer recipe incomplete; key results are model-dependent.

## Links

- Method: (cite: Schoeier01) (radiative transfer code)
- Method: (cite: Schoeier00) (intensity ratio to isotope ratio relation)
- Companion: (cite: Maercker12) (12CO(3-2) results from the same ALMA dataset and spiral discovery)

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 44,
  "rate": 0.629
 },
 "evidence_ok": true
}
```
