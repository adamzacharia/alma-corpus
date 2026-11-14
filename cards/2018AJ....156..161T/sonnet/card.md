# ALMA Thermal Observations of Europa

`2018AJ....156..161T` | The Astronomical Journal 2018 | first author: Trumbo, Samantha K. | arXiv: 1808.07111 | DOI: 10.3847/1538-3881/aada87

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: What causes the large-scale daytime thermal structure of Europa, and do surface thermal properties (thermal inertia) vary spatially?  
  > "We use a global thermal model of Europa to simulate the ALMA observations in order to investigate the thermal structure visible in the data." (abstract)
- Target **Europa**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01302.S
- bands: Band 6, near 230 GHz (233 GHz, 1.3 mm)  
  > "The observations presented here were taken in Band 6, near 230 GHz, in the “continuum” (or “TDM”) mode, with the standard frequency tuning." (ALMA Observations and Data Reduction)
- frequencies and spectral setup: four SPWs: 223–225, 225–227, 239–241, 241–243 GHz; averaged, 233 GHz used  
  > "This results in four spectral windows with frequencies: 223–225 GHz; 225–227 GHz; 239–241 GHz; and 241–243 GHz." (ALMA Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: 12-m main array, 38–43 antennas  
  > "For these observations, there were between 38 and 43 antennas, in the C36-7 configuration." (ALMA Observations and Data Reduction)
- configurations: C36-7  
  > "there were between 38 and 43 antennas, in the C36-7 configuration." (ALMA Observations and Data Reduction)
- baselines: max ~5 km  
  > "This configuration has a maximum antenna spacing of $\sim$5 km, giving a resolution on the sky of $\sim$50 milliarcseconds." (ALMA Observations and Data Reduction)
- angular resolution: ~50 mas; beams 42–77 mas (~200 km linear)  
  > "2015 Nov 26 | 08:22/08:38 | 210–211.1 | -1.52 | 77/52" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~20 min per observation, ~8 min on Europa  
  > "Each observation was about 20 minutes in duration, including all calibration overheads, which resulted in roughly 8 minutes on Europa." (ALMA Observations and Data Reduction)
- observing dates: 2015 Nov 17, 25, 26, 27  
  > "We observed Europa with ALMA on November 17, 25, 26, and 27 of 2015." (ALMA Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Other facility **Voyager/Galileo**: albedo measurements and global mosaic used to build albedo map  
  > "we take these as tie-points to the greyscale *Voyager*/*Galileo* global mosaic of Europa (cite: USGSmap)." (Thermal Modeling)
- External data: Voyager normal albedos at discrete locations  
  > "We take the normal albedos for distinct locations on the surface from (cite: McEwen1986) across the green, blue, violet, and ultraviolet Voyager filters." (Thermal Modeling) [from (cite: McEwen1986)]
- External data: Voyager/Galileo global mosaic  
  > "greyscale *Voyager*/*Galileo* global mosaic of Europa (cite: USGSmap)" (Thermal Modeling) [from (cite: USGSmap)]
- Simulation/model as data: Global 1-D thermal model simulating ALMA images  
  > "We use a global thermal model of Europa, similar to those used for other Solar System bodies" (Thermal Modeling)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA, then AIPS  
  > "Initial calibration of the data was provided by the ALMA observatory and completed in the CASA reduction package" (ALMA Observations and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1058+0133  
  > "The point-like calibrator J1058+0133 was used as the absolute flux density scale calibrator for all four observations" (ALMA Observations and Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: three iterations down to 8 s, initial limb-darkened model  
  > "We self-calibrated (cite: 1999_Cornwell) the data in three iterations down to a time interval of 8 seconds" (ALMA Observations and Data Reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0  
  > "They were produced using a robust parameter of 0, which is a good compromise between resolution and signal-to-noise." (ALMA Observations and Data Reduction)
- uv taper: _not stated_
- cell size: ~1/10 of resolution  
  > "Pixel sizes are roughly a factor of 10 smaller than the actual resolution to minimize deconvolution errors." (ALMA Observations and Data Reduction)
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

- Full thermal model description  
  > "A complete description of the model can be found in (cite: Trumbo2017alma)." (Thermal Modeling) [from (cite: Trumbo2017alma)]
- Albedo adjustment near Pwyll  
  > "If we apply the same minor albedo adjustment near Pwyll as (cite: Trumbo2017alma)" (Fits to ALMA Observations) [from (cite: Trumbo2017alma)]

### Not stated but needed to reproduce (our reading)

- Imaging software/task details and deconvolution settings in AIPS
- Exact best-fit emissivity and thermal inertia ranges (values missing in text)
- Thermal model code and numerical settings (layers, time step)
- Flux scale uncertainty
- Image sizes and beam-correction details

## Analysis recipe

1. **Calibrate, self-calibrate and image**: Pipeline calibration in CASA, self-cal in AIPS with limb-darkened model, imaging robust 0  
  > "We exported the provided visibilities from CASA and continued the data reduction in the AIPS reduction package" (ALMA Observations and Data Reduction)
   - software: CASA, AIPS
   - fitting: _not stated_
   - validation: _not stated_
2. **Build albedo map**: Linear fit of mosaic pixel values to Voyager albedo tie-points  
  > "We fit a line to the relationship between the pixel values in the image at the Voyager albedo locations and the approximate bolometric albedo tie-points" (Thermal Modeling)
   - fitting: linear fit  
  > "We fit a line to the relationship between the pixel values in the image at the Voyager albedo locations and the approximate bolometric albedo tie-points" (Thermal Modeling)
   - validation: R^2 of 0.92, albedo std 0.03  
  > "The pixel values and albedo tie-points correlate with an R$^2$ of 0.92 and a standard deviation in albedo of 0.03." (Thermal Modeling)
3. **Global fit of thermal inertia and emissivity**: Grid search minimizing squared residuals between model and data images  
  > "We simulate the four ALMA observations over a grid of thermal inertias and emissivities and find the single best-fit values to these data by minimizing the square of the residuals" (Fits to ALMA Observations)
   - parameter: heat flux 20 mW/m^2 lower boundary  
  > "using a small global heat flux of 20 $mW/m^2$" (Thermal Modeling)
   - fitting: grid search, least squares  
  > "We simulate the four ALMA observations over a grid of thermal inertias and emissivities and find the single best-fit values to these data by minimizing the square of the residuals between model and data images." (Fits to ALMA Observations)
   - validation: residual images  
  > "Figure [2](#fig:residuals) shows the residuals between each data-model image pair from Figure [1](#fig:datamodel)" (Fits to ALMA Observations)
4. **Map thermal inertia**: Fix emissivity 0.75, fit thermal inertia at each point within 57 deg of image center; both times used in overlaps  
  > "we only fit data within 57$\degree$ of the central point of each observation" (Fits to ALMA Observations)
   - assumption: All residuals attributed to thermal inertia variations  
  > "Under the assumption that all of the residuals between the ALMA data and the global best-fit model can be attributed to thermal inertia variations" (Fits to ALMA Observations)
   - fitting: per-pixel fit  
  > "We fix the emissivity at the global best-fit value of 0.75 and fit the data by letting the thermal inertia vary at each point." (Fits to ALMA Observations)
   - validation: remaining discrepancies mostly ≤3 K; Pwyll consistent with PPR  
  > "minor discrepancies (primarily $\leq$ 3 K) remain" (Fits to ALMA Observations)

## Software

- **CASA** : initial calibration  
  > "completed in the CASA reduction package" (ALMA Observations and Data Reduction)
- **AIPS** : self-calibration and imaging  
  > "continued the data reduction in the AIPS reduction package" (ALMA Observations and Data Reduction)
- **ALMA pipeline** : initial calibration  
  > "via the ALMA pipeline" (ALMA Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Global best-fit emissivity | 0.75 | not stated | dimensionless | 3 | We fix the emissivity at the global best-fit value of 0.75 |
| Albedo map fit R^2 | 0.92 | not stated | dimensionless | 2 | correlate with an R$^2$ of 0.92 |
| Anomalous high thermal inertia region location | 90 W, 23 N | not stated | degrees | 4 | near 90$\degree$ W and 23$\degree$ N |

## Qualitative findings

- Albedo variations explain most large-scale daytime thermal structure  
  > "the majority of the visible daytime thermal structure on Europa is governed primarily by local albedo variations" (Fits to ALMA Observations)

## Claim tuples

- H: Daytime thermal structure is driven by albedo | E: Homogeneous thermal model with Voyager-based albedo map compared to four ALMA images | R: Model reproduces large-scale structure well, with localized residuals | F: Albedo dominates; residuals suggest thermal property variations | **supported**
- H: Residuals reflect thermal inertia variations | E: Per-pixel thermal inertia fit with fixed emissivity | R: Map with an anomalous high-inertia region near 90W, 23N | F: Region appears truly distinct but origin speculative | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Sunlight penetration, emission depth and roughness tested; little effect on conclusions  
  > "has little effect on our conclusions from the data" (Thermal Modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): Cannot distinguish thermal inertia, emissivity, albedo causes without multiple times of day  
  > "we cannot conclusively distinguish between these potential causes everywhere" (Fits to ALMA Observations)
- Caveat (inferred, ours): Thermal inertia degenerate with emissivity and albedo errors
- Caveat (inferred, ours): No formal uncertainties on fitted parameters

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Thermal model code
- Missing: Numeric fitted values and uncertainties
- Missing: AIPS imaging parameters
- Data volume (inferred): ~tens of GB
- Score (inferred): 4/5, Data public project known but model code and key numbers not given.
- Rediscovery candidate: no, Model is unreleased and key values are missing.

## Links

- Method: (cite: Trumbo2017alma) (full thermal model description)
- Companion: (cite: Trumbo2017alma) (earlier ALMA Europa thermal analysis)

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
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
  "stated": 38,
  "rate": 0.551
 },
 "evidence_ok": true
}
```
