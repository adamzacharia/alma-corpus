# The Nuclear Filaments inside the Circumnuclear Disk in the Central 0.5 pc of the Galactic Center

`2019ApJ...885L..20H` | The Astrophysical Journal Letters 2019 | first author: Hsieh, Pei-Ying | arXiv: 1910.07559 | DOI: 10.3847/2041-8213/ab4e1e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism
- Question: Is the molecular inflow channeled past the CND? What are the structure and kinematics of the gas in the inner cavity of the CND (nuclear filaments)?  
  > "”Is the molecular inflow able to be channeled past the CND?”" (Introduction); "The primary goal is to find and characterize the gas structure in the inner cavity of the circumnuclear disk (CND) in high resolution" (abstract)
- Target **Galactic Center (Sgr A*, CND and nuclear filaments)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00040.S
- bands: _not stated_
- frequencies and spectral setup: CS(7-6) 342.882 GHz; default channel width 244.141 kHz  
  > "The default channel width of the spectral windows was 244.141 kHz." (ALMA Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: 43 12-m antennas, 7 m, and total-power array  
  > "we combined the 12 m, 7 m, and single-dish data." (ALMA Observations and Data Reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: native 0.8'', smoothed to 1.3'' (0.05 pc)  
  > "The native resolution of the CS(7-6) map is 0.8$\ensuremath{''}$." (ALMA Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 11 mJy noise in smoothed map  
  > "The noise level is 11 mJy of the smoothed map." (ALMA Observations and Data Reduction)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CS J=7-6 (342.882 GHz)
- External data: Enclosed mass M(r) of stars and Sgr A* used for Keplerian curves  
  > "The enclosed mass $M(r)$ is adopted from the literature (cite: genzel10) to account for the total mass of the enclosed stars and Sgr A\* (cite: ghez08)." (Results) [from (cite: genzel10); (cite: ghez08)]
- External data: Filament mass of 5 Msun  
  > "To create the nuclear filaments with a mass of 5 $M_{\odot}$ (cite: moser17)" (Discussion) [from (cite: moser17)]

## Processing

### Calibration

- pipeline or manual: pipeline and manual reduction script for cycle-5 data  
  > "Calibration of the raw visibilities was performed with the pipeline and manual reduction script for the cycle-5 data" (ALMA Observations and Data Reduction)
- casa version: CASA v5.1.1-5  
  > "(CASA v5.1.1-5)" (ALMA Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: Tclean for deconvolution, Feather for merging with single dish  
  > "The CASA tasks Tclean and Feather were used to deconvolve and merge the interferometric and single-dish maps." (ALMA Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "We used the Briggs robust parameter of 0.5." (ALMA Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Mstransform  
  > "The task Mstrasform was used to subtract the continuum emission." (ALMA Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12 m + 7 m + single-dish; four mosaics processed separately then combined  
  > "We processed the four individual mosaics separately, and combined them into one map." (ALMA Observations and Data Reduction)
- smoothing: smoothed to 1.3'' (0.05 pc); 2 km/s channels  
  > "we smoothed the maps to 1.3$\ensuremath{''}$ ($=0.05$ pc)" (ALMA Observations and Data Reduction)
- final beam: _not stated_
- final rms: 11 mJy (smoothed map)  
  > "The noise level is 11 mJy of the smoothed map." (ALMA Observations and Data Reduction)

### Inherited from earlier work

- Rotating ring model with circular orbits for the CND  
  > "we start this analysis with the simplest rotating ring model (cite: guesten87; jackson93; martin12)." (Results) [from (cite: guesten87; jackson93; martin12)]

### Not stated but needed to reproduce (our reading)

- Total-power and 12m/7m configurations, observing dates, and integration times
- Feather parameters (SD scale factor) and tclean cleaning threshold, mask, cell and image size
- Line-free channels for continuum subtraction
- Distance to GC and exact M(r) function used
- Chi-square definition, uncertainties, and how phase-plot data points were extracted
- Flux calibrators and flux scale uncertainty
- Position of Sgr A* used as center

## Analysis recipe

1. **Calibrate, image and combine 12m, 7m and single-dish data**: Pipeline/manual calibration, tclean mosaic of four fields, Feather with single dish, continuum subtraction, smoothing to 1.3''  
  > "The CASA tasks Tclean and Feather were used to deconvolve and merge the interferometric and single-dish maps." (ALMA Observations and Data Reduction)
   - software: CASA, tclean, feather, mstransform
   - parameter: robust 0.5; 2 km/s channels; smoothed to 1.3''  
  > "The image cubes were made at a velocity resolution of 2 km s$^{-1}$ to enhance the signal-to-noise ratio." (ALMA Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Make moment maps**: Integrated intensity (MOM0) and intensity-weighted velocity (MOM1) maps  
  > "Figure [1](#fig-m0) displays the integrated CS(7-6) intensity maps (MOM0) in the inner region of the CND." (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit Keplerian circular orbits at five radii**: Grid search over inclination, position angle and radial velocity minimizing chi^2 of V_los against phase plots  
  > "The best-fit circular orbits of the line-of-sight velocity $V_{\rm los}$ determined by the mininum $\chi^2$" (Results)
   - parameter: radii 0.5, 0.4, 0.35, 0.25, 0.15 pc; inclination 5-80 deg step 5; PA 70-150 deg step 5; radial velocity 0-120 km/s step 10  
  > "The free parameters with their fitting ranges are the inclination (5$\ensuremath{^\circ}$-80$\ensuremath{^\circ}$ in steps of 5$\ensuremath{^\circ}$)" (Results)
   - assumption: Keplerian motion around enclosed mass M(r) from literature; points separated by one beam are independent  
  > "The data points at the different radii for fitting are chosen with a separation of one beam size, and can thus be considered as being independent." (Results)
   - fitting: Minimum chi^2 grid search  
  > "determined by the mininum $\chi^2$" (Results)
   - validation: Compared with higher-inclination (65-80 deg) models, which fail to explain features  
  > "A higher inclination (65$\ensuremath{^\circ}$ to 80$\ensuremath{^\circ}$) is not able to explain the gross feature within the radius of 0.5 pc." (Results)
4. **Estimate eccentricity from radial/tangential velocity ratio**: Eccentric Keplerian orbit relation V_rad/V_tan = e sin(theta)/(1+e cos(theta))  
  > "we obtain $e \geq$ 0.6 and $\theta \geq 60^\circ$ (i.e., far from the periapsis of Sgr A\*) to match the ${V_{\rm rad}}/{V_{\rm tan}}$ ratio." (Discussion)
   - parameter: V_rad=120 km/s, V_tan=200 km/s  
  > "Using $V_{\rm rad}$=120 km s$^{-1}$ and $V_{\rm tan}$= 200 km s$^{-1}$" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** v5.1.1-5: calibration, tclean, feather, mstransform  
  > "Common Astronomy Software Applications (CASA v5.1.1-5)" (ALMA Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Nuclear filament inclination | ~10-20 | not stated | deg | 3 | inclination angle of $\sim10\ensuremath{^\circ}-20\ensuremath{^\circ}$ (radius $\le$ 0.5 pc) |
| Inward radial velocity of E1-E3, W1-W3 | 90-120 | not stated | km/s | 3 | inward radial velocities (90-120 km s$^{-1}$) of E1-E3 and W1-W3 |
| Eccentricity lower limit | e >= 0.6 | not stated | dimensionless | 4 | we obtain $e \geq$ 0.6 |
| Dynamical timescale at 0.25 pc | 5600 | not stated | years | 0 | the dynamical time scale of the nuclear filaments is 5600 years at a radius of 0.25 pc |
| Accretion time 0.55 to 0.15 pc | 7800 | not stated | years | 0 | it takes about 7800 years to accrete from 0.55 to 0.15 pc |

## Qualitative findings

- Nuclear filaments rotate in the same sense as the CND about Sgr A*  
  > "we find that the nuclear filaments are rotating in the same sense as the CND" (Summary)

## Claim tuples

- H: Do the nuclear filaments share the CND geometry? | E: Keplerian circular orbit fits at five radii to CS(7-6) phase plots | R: Inclination 10-20 deg versus 65-80 deg for the CND | F: Nuclear filaments are nearly face-on, implying a warped structure from CND to filaments | **supported**
- H: Are the filaments purely Keplerian? | E: Compare the single-orbit fit with the data at 0.4 and 0.5 pc | R: Single Keplerian orbit cannot fit all features at 0.4 and 0.5 pc | F: Deviation is likely from inward radial motion or multiple orbits | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Filaments might have CND-like inclination but be sub-Keplerian due to radiation and thermal pressure  
  > "their low projected velocities are sub-Keplerian due to radiation and thermal pressure" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Regions filled with nuclear filaments are small, so shear and non-rotating clumps could be present  
  > "We note that the regions filled with nuclear filaments are still rather small." (Results)
- Caveat (inferred, ours): Low inclination relies on the assumption of Keplerian motion
- Caveat (inferred, ours): No uncertainties on fitted parameters; coarse grid
- Caveat (inferred, ours): Small number of independent points per radius

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Feather and tclean details
- Missing: Fitting data point selection and chi^2 specifics
- Missing: Enclosed mass function
- Data volume (inferred): ~hundreds of GB to 1 TB (four 150-pointing mosaics, 12m+7m+TP)
- Score (inferred): 4/5, Imaging recipe is brief and the fitting is only loosely specified, but the project code is given and the result is simple.
- Rediscovery candidate: no, The paper does not state that the data are public, and the fitting details are incomplete.

## Links

- Companion: (cite: moser17) (Earlier ALMA CS(5-4) of the central association)
- Companion: (cite: hsieh17) (Earlier team work on CND streamers)

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
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
  "facts": 66,
  "stated": 30,
  "rate": 0.455
 },
 "evidence_ok": true
}
```
