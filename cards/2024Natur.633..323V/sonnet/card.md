# One month convection timescale on the surface of a giant evolved star

`2024Natur.633..323V` | Nature 2024 | first author: Vlemmings, Wouter | arXiv: 2409.06785 | DOI: 10.1038/s41586-024-07836-9

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, stellar_physics
- Question: What are the size and timescale of convective surface structures on the AGB star R Doradus, as imaged with ALMA at submillimeter wavelengths?  
  > "Here we report a series of reconstructed interferometric images of the surface of the evolved giant star R Doradus." (abstract)
- Target **R Doradus**: coordinates _not stated_; z/distance 55±3 pc  
  > "The distance to R Doradus has been determined to be $55\pm3$ pc using revised *Hipparcos* measurements (cite: 2007A&A...474..653V)." (Methods: Source properties); distance from revised Hipparcos (van Leeuwen 2007)  
  > "The distance to R Doradus has been determined to be $55\pm3$ pc using revised *Hipparcos* measurements (cite: 2007A&A...474..653V)." (Methods: Source properties)

## Data provenance

- ALMA projects: 2022.1.01071.S
- bands: Band 7 (~338 GHz) and Band 6 (~225 GHz)  
  > "The AGB star R Doradus was observed in ALMA Bands 6 and 7" (Methods: Observations, data reduction and imaging)
- frequencies and spectral setup: Band 7: four spws at 331.2, 333.0, 342.1, 345.1 GHz, 1.875 GHz each, 1920 channels; Band 6: 218.9, 220.8, 230.0, 232.9 GHz  
  > "Each spw had a bandwidth of $1.875$ GHz and 1920 channels." (Methods: Observations, data reduction and imaging)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C-9 and C-10  
  > "The observations were taken in the largest ALMA configurations (C-9 and C-10)" (Methods: Observations, data reduction and imaging)
- baselines: Max baselines 9.2-16.2 km for Band 7 epochs (min 113-230 m)  
  > "| 27-07-2023 | 0:36/0:10 | 230/16196 | $12.2\times9.1, -23.4$ | $0.51$ |" (Table 1)
- angular resolution: 8-25 mas (superuniform weighting)  
  > "this allowed us to reconstruct images of the stellar surface at an angular resolution between $8-25$ mas" (main text)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Band 7: 5 Jul-2 Aug 2023; Band 6: 17 Aug 2023  
  > "| 17-08-2023 | 00:59/00:22 | 83/14852 | $18.7\times14.6, 34.4$ | $0.05$ |" (Table 1)
- pi or archival as stated: _not stated_
- External data: Distance 55±3 pc  
  > "The distance to R Doradus has been determined to be $55\pm3$ pc using revised *Hipparcos* measurements" (Methods: Source properties) [from (cite: 2007A&A...474..653V)]
- External data: Infrared stellar diameter 51.18±2.24 mas  
  > "$D_{\rm
  IR}=51.18\pm2.24$ mas (cite: 2019ApJ...883...89O)" (Methods: Source properties) [from (cite: 2019ApJ...883...89O)]

## Processing

### Calibration

- pipeline or manual: Last three epochs ALMA pipeline; first two epochs manual by Nordic ARC node staff  
  > "The calibration of the last three epochs was performed using the ALMA pipeline in CASA v6.4.1.12 ." (Methods: Observations, data reduction and imaging)
- casa version: CASA 6.4.1.12 (pipeline); 6.5.4.9 (manual)  
  > "calibration was performed manually by staff from the Nordic ALMA regional center node using CASA v6.5.4.9" (Methods: Observations, data reduction and imaging)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0519-4546 (bandpass/amplitude)  
  > "the quasars J0519-4546 and J0516-6207 as bandpass/amplitude and phase calibrator, respectively" (Methods: Observations, data reduction and imaging)
- flux scale uncertainty: _not stated_
- self calibration: Two steps of phase-only self-calibration on stellar continuum; SNR improved ~2.5  
  > "two steps of phase-only self-calibration was performed on the stellar continuum." (Methods: Observations, data reduction and imaging)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: superuniform weighting (compared with Briggs robust 0.5)  
  > "images, using all four spw, were produced for the five epochs using *superuniform* visibility weighting" (Methods: Observations, data reduction and imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Smoothing to the largest beam was tested and smooths out structures; highest-resolution images used  
  > "reducing the angular resolution to match that of the epoch with the largest beam smooths out the observed structures and the derived velocities" (Methods: Observations, data reduction and imaging)
- final beam: Epoch beams from 24.4x13.3 to 12.3x8.3 mas (Table 1)  
  > "| 02-08-2023 | 1:41/0:36 | 230/16196 | $12.3\times8.3, -29.7$ | $0.31$ |" (Table 1)
- final rms: 0.14, 0.19, 0.38, 0.51, 0.31 mJy/beam for the five Band 7 epochs  
  > "| 18-07-2023 | 0:39/0:11 | 230/15238 | $15.8\times8.8, 39.6$ | $0.38$ |" (Table 1)

### Not stated but needed to reproduce (our reading)

- tclean parameters (cell, image size, niter, threshold, masking)
- superuniform weighting parameters (e.g. npixels)
- which channels/lines were flagged
- self-calibration solution intervals
- uvmultifit model setup and uv bin widths in PSD
- method for deriving half-power radius vs position angle and velocity uncertainty
- stellar mass/Teff details for the escape velocity
- PSD peak-fitting method

## Analysis recipe

1. **Calibrate and image continuum**: Pipeline/manual calibration, line flagging, averaging, phase-only self-cal, superuniform-weighted imaging  
  > "molecular lines were identified and flagged before the data was averaged to an integration time of 6.06 s and to 50 channels per spw." (Methods: Observations, data reduction and imaging)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared Band 7 epochs with independent Band 6 observations  
  > "Since the different observations are completely independent, this shows that the pattern seen in the radii is intrinsic to the source" (Methods: Band 6 observations)
2. **Fit stellar disc in visibilities**: uv-fit of a nearly circular disc to the last three epochs combined  
  > "Using a combination of the last three epochs, we fit a nearly circular stellar disc" (Methods: Source properties)
   - software: uvmultifit
   - assumption: top-hat disc profile  
  > "how well a top-hat shaped stellar disc profile fits the observations" (Methods: Stellar disc profile)
   - fitting: _not stated_
   - validation: Radial profile compared with a beam-convolved top-hat model; residuals ~2% of peak  
  > "with residuals at a level of $\sim 2\%$ of the peak emission" (Methods: Stellar disc profile)
3. **Spatial PSD of surface structure**: Subtract disc from visibilities, compute |V|^2 in annular uv-distance bins; compare on-source with an off-source PSD at 7 arcsec offset  
  > "We chose an offset of $7$ arcseconds to avoid a contribution to the off-source PSD from the source signal." (Methods: Spatial Power Spectral Density analysis)
   - software: uvmultifit
   - fitting: _not stated_
   - validation: Off-source PSD identifies correlated noise  
  > "By comparing the on- and off-source PSD we can determine which structures are significant and which are possibly due to correlated noise in the visibilities." (Methods: Spatial Power Spectral Density analysis)
4. **Limb radius and surface velocity**: Half-power radius vs position angle in highest-resolution epochs; differences between consecutive epochs give velocity  
  > "By determining the difference in radius between consecutive epochs at every position angle, we can derive the average velocity profile of the 338 GHz optical depth surface" (main text)
   - fitting: _not stated_
   - validation: Band 6 radii show similar features  
  > "also the 225 GHz observations show similar features confirming that they are intrinsic to the star" (main text)
5. **Convective timescale and comparison with theory**: t_surf ~ x/ΔV; compare size with x = α H_p relation and fit α  
  > "$t_{\rm
  surf}\sim x/\Delta V = 33\pm3$ days" (main text)
   - assumption: Teff=2710±70 K, log g=-0.6±0.1, d=55 pc  
  > "we adopt the values for the effective temperature of $T_{\rm eff}=2710\pm70$ K." (Methods: Source properties)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.4.1.12 and 6.5.4.9: Calibration, self-calibration and imaging  
  > "calibration was performed manually by staff from the Nordic ALMA regional center node using CASA v6.5.4.9" (Methods: Observations, data reduction and imaging)
- **uvmultifit** : uv-plane fitting of stellar disc  
  > "we first use the $uv-$fitting code *uvmultifit* to fit the stellar disc" (Methods: Spatial Power Spectral Density analysis)
- **python** : analysis  
  > "This paper makes use of the NRAO CASA package and python." (Code availability)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dominant structure size | 0.72 | 0.05 | au | 3 | $0.72\pm0.05$ astronomical units (au) |
| Dominant structure angular size | 13.1 | 0.6 | mas | 3 | $x=13.1\pm0.6$ mas |
| Surface velocity range | -18 to +20 | not stated | km/s | 4 | vary between $-18$ and $+20~$km s$^{-1}$ |
| Surface readjustment timescale | 33 | 3 | days | 5 | $t_{\rm
  surf}\sim x/\Delta V = 33\pm3$ days |
| 338 GHz disc radius | 1.64 | 0.09 | au | 2 | $R_{\rm 338GHz} =
1.64\pm0.09$ au |
| Brightness temperature at 338 GHz | 2270 | 130 | K | 2 | $T_b=2270\pm130$ K |
| 338 GHz disc flux density | 521 | 18 | mJy | 2 | $F_{\rm 338GHz}=521\pm18$ mJy |
| Scaling parameter alpha | 17 | +5/-3 | dimensionless | 5 | we can estimate a value of $\alpha=17^{+5}_{-3}$ |
| Brightness temperature increase from shocks | ~700-1500 | not stated | K | 5 | We find $\Delta T_b$ to be between $\sim700$ and $1500$ K. |

## Qualitative findings

- Surface structures have lifetimes of at least three weeks and are intrinsic to the star  
  > "we find that the structures we observe at the surface have a typical lifetime of at least three weeks." (main text)

## Claim tuples

- H: Do ALMA images resolve convective structure on an AGB star's surface and what is its scale? | E: PSD analysis of Band 7 visibilities after disc subtraction | R: Dominant size 0.72±0.05 au | F: Granule size matches parametric formulae for AGB stars | **supported**
- H: What is the convective timescale? | E: Epoch-to-epoch radius changes give velocities; t=x/ΔV | R: 33±3 days, ~30% of extrapolated Tremblay formula | F: AGB convection differs from higher-mass/less-evolved stars | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Chance alignment of convective cells explaining rotation ruled out by multi-year observations  
  > "hence a chance alignment of convective cells can be ruled out." (Methods: Source properties)
- How they decided it was enough: _not stated_
- Limitation (authors): Observed motions depend on density, temperature, ionisation and velocity changes; velocities are lower limits  
  > "They thus represent a lower limit to the actual gas velocities." (main text)
- Caveat (inferred, ours): Velocity from optical-depth surface motion is not a direct gas velocity
- Caveat (inferred, ours): Only two AGB measurements constrain alpha
- Caveat (inferred, ours): First two epochs have poorer quality
- Caveat (inferred, ours): Cadence of ~weeks limits sampling of timescales

## Reproducibility

- Data public (paper): Public in ALMA archive, project 2022.1.01071.S  
  > "The ALMA data are publicly available on the ALMA archive (<https://almascience.eso.org/aq/>) as part of project 2022.1.01071.S." (Data availability)
- Products in archive: _not stated_
- Code: uvmultifit is public; derived CSV source data released; no analysis scripts  
  > "The code used for $uv$-fitting *’uvmultifit’* is publicly available." (Code availability)
- Missing: tclean settings
- Missing: self-cal parameters
- Missing: radius/velocity extraction algorithm
- Missing: PSD binning and peak fitting details
- Data volume (inferred): ~hundreds of GB to ~1 TB raw for six long-baseline epochs
- Score (inferred): 3/5, Public data and CSV outputs, but key imaging and extraction parameters are unstated.
- Rediscovery candidate: no, Recipe lacks details for the radius/velocity and PSD extraction.

## Links

- Companion: (cite: 2018A&A...613L...4V) (Previous ALMA observations showing R Dor rotation)

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
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 38,
  "rate": 0.551
 },
 "evidence_ok": true
}
```
