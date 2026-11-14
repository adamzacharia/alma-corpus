# ALMA and IRIS Observations of the Solar Chromosphere. II. Structure and Dynamics of Chromospheric Plages

`2021ApJ...906...83C` | The Astrophysical Journal 2021 | first author: Chintzoglou, Georgios | arXiv: 2012.05970 | DOI: 10.3847/1538-4357/abc9b0

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: sun, solar_system
- Question: How do ALMA Band 6 brightness temperatures in chromospheric plage relate to IRIS Mg II, C II and Si IV diagnostics, where does the 1.25 mm emission form, and does it show shock heating?  
  > "We investigate the high degree of similarity between chromospheric plage features observed in *ALMA*/Band6 (at 1.25 mm wavelength) and *IRIS*/Si IV at 1393 Å." (abstract)
- Target **Plage region in leading part of NOAA AR12651**: coordinates N11 E17; (x,y)=(-260", 265") helioprojective  
  > "We observed a plage region in the leading part of NOAA AR12651 on 22-Apr-2017, at heliographic coordinates N11$\ensuremath{^\circ}$E17$\ensuremath{^\circ}$" (2 Observations and Modeling); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00050.S
- bands: Band 6, averaged to 1.25 mm  
  > "Such averaging results to Band6 maps at $\lambda$=1.25 mm." (APPENDIX)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam ≈0.7"×0.8"  
  > "*ALMA*/Band6 (beam size $\approx$0.7$''$$\times$0.8$''$)" (6 Summary & Conclusions)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 34 min time series, 2 s cadence  
  > "From our 34 min-long time series we calculate the autocorrelation at each pixel in the Mg II FOV" (4.2)
- observing dates: 22-Apr-2017  
  > "We observed a plage region in the leading part of NOAA AR12651 on 22-Apr-2017" (2 Observations and Modeling)
- pi or archival as stated: _not stated_
- Line: Mg II k k2v,k2r,k3 (IRIS) (2796.35 Å)
- Line: Si IV IRIS 1393 Å (1393 Å)
- Other facility **IRIS**: Mg II, C II, Si IV rasters and SJI images  
  > "we perform an intercomparison between wavelength-integrated rasters in Si IV 1393 Å, and C II 1335 Å, Mg II k 2796 Å and also with *ALMA*/Band6." (4.1.1)
- Other facility **SDO/HMI**: photospheric magnetograms for plage definition  
  > "we overplot on the *SDO*/HMI map the regions of plage within red contour" (3)
- External data: Bifrost 2.5D plage simulation and synthetic ALMA/IRIS observables  
  > "Additional details regarding the simulation and the synthesis of observables can be found in Paper I and in (cite: Martinez-Sykora_etal_2020b)." (2.2) [from (cite: Martinez-Sykora_etal_2020b)]
- Simulation/model as data: Bifrost 2.5D simulation with ambipolar diffusion and non-equilibrium ionization, synthetic Band6, Mg II, Si IV  
  > "We employed a 2.5D numerical simulation (Bifrost model) of a plage region considering ambipolar diffusion in non-equilibrium ionization conditions." (6 Summary & Conclusions)

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
- smoothing: IRIS maps convolved with Band6 beam and position angle each frame; 4-pixel binning along slit  
  > "we degrade the wavelength-integrated *IRIS* raster maps by convolving them with the Band6 beam size and respective position angle at each time frame of our series." (4.1.1)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Reduction of IRIS and ALMA observations  
  > "For additional details regarding the reduction of the *IRIS* and *ALMA* observations used here refer to § 2 of Paper I." (2 Observations and Modeling) [from Paper I; Chintzoglou et al 2020a]
- Simulation and synthesis details  
  > "Additional details regarding the simulation and the synthesis of observables can be found in Paper I and in (cite: Martinez-Sykora_etal_2020b)." (2.2) [from Paper I; (cite: Martinez-Sykora_etal_2020b)]
- Double Gaussian fitting of Mg II  
  > "we perform double gaussian fitting (cite: Schmit_etal_2015) for the Mg II raster data" (4.1.1) [from (cite: Schmit_etal_2015)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, CASA version, imaging parameters (all in Paper I)
- IRIS/ALMA co-alignment procedure
- Bifrost output snapshots
- Fitting details for double Gaussian
- Autocorrelation lifetime definition
- Pore mask construction details

## Analysis recipe

1. **Define plage and periphery masks**: Magnetogram threshold ±0.1 kG as guide; pore removed with Band6 Tb≥6,500 K mask  
  > "we employ the *ALMA*/Band6 maps segmented at a low threshold $T_b\ge6,500$ K." (3)
   - fitting: _not stated_
   - validation: Results change only 3-5% with thresholded magnetogram masks  
  > "if we impose thresholded magnetogram masks for the plage areas the results do not change beyond 3-5%" (4.1.1.1)
2. **Build matched IRIS rasters and radiative temperatures**: Match Band6 2 s frames to slit times within ±1 s; Mg II Trad via Planck inversion; Si IV and C II integrated; hot pixels >10 DN/s interpolated  
  > "we match our *ALMA*/Band6 2 s-cadence series by composing “rasters” that match the time of each slit sampling position to within $\pm$1 s." (4.1.1)
   - fitting: Double Gaussian for Mg II features  
  > "we perform double gaussian fitting (cite: Schmit_etal_2015) for the Mg II raster data" (4.1.1)
   - validation: Mid-raster frame matching changes results ~1%  
  > "but found no significant change in our results (i.e., of order $\sim$ 1%)" (4.1.1)
3. **Correlate observables**: Pearson C.C. in plage, periphery and full FOV (time-averaged), and per correlation bin per time step  
  > "We proceed by calculating the linear correlation coefficent (Pearson r, hereafter “C.C.”) between each of the four observables" (4.1.1.1)
   - fitting: _not stated_
   - validation: Same analysis on Bifrost synthetic observables  
  > "we perform this analysis on the synthetic observables produced from our model." (4.1.2)
4. **Explain formation heights with Bifrost**: Inspect emissivity and tau=1 heights of synthetic Si IV, Mg II k, Band6 in spicule and fibril regions  
  > "we explore the time evolution in the emission and formation height of the synthetic observables for the region with spicules and plage" (4.1.3)
   - assumption: Vertical LOS, simulation degraded to IRIS and Band6 resolution  
  > "The viewing geometry chosen was for an “observer” looking from above down on the domain" (2.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **Shock heating in plage**: Autocorrelation map to select 1"×1" region; λ-t plots with unsharp mask and time derivatives; overplot ALMA Tb  
  > "we filter them with an unsharp-mask image processing operation with a 5-pixel radius." (4.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| C.C. ALMA Tb vs Mg II k Trad, plage | 0.56 | not stated | dimensionless | 3 | While the C.C. for *ALMA*/Band6 $T_b$ with Mg II k $T_{\rm rad}$ is 0.56 for plage and 0.57 for the periphery |
| C.C. ALMA vs Mg II k, full FOV | 0.74 | not stated | dimensionless | 3 | the calculation for the full FOV increases the value dramatically, to a C.C. of 0.74 |
| C.C. with Mg II h2v/h2r average Trad method | 0.52 | not stated | dimensionless | 3 | we found that the C.C. in that case was even lower, i.e., C.C. = 0.52 |
| Plage pixels | 650 (578 after pore exclusion); periphery 480 | not stated | pixels | 1 | The total number of pixels in the plage mask is 650 which finally becomes 578 pixels after excluding the pore region |
| Baseline Tb above plage | ≈7,500 K (max 8,500 K) | not stated | K | 5 | The jumps in T$_b$ are of order 10%-20% increase from a baseline value of $\approx$ 7,500 K (maximum jump at 8,500 K). |
| Shock decay time | 60-120 | not stated | s | 5 | The observed decay time down to the baseline value is of order $\approx$60-120 s. |

## Qualitative findings

- ALMA Band6 emission and Si IV delineate the same upper parts of spicules and dynamic fibrils; Mg II k is weakly or anti-correlated due to absorption.  
  > "We conclude that the apparent anti-correlation or lack of correlation has its origin in Mg II opacity effects in plage structures." (6 Summary & Conclusions)

## Claim tuples

- H: ALMA Band6 forms in the low-to-mid chromosphere and correlates well with Mg II | E: Pearson C.C. between ALMA Tb and IRIS observables in cleanly defined plage, with Bifrost comparison | R: C.C. with Mg II 0.49-0.56; highest among Si IV, C II and ALMA | F: ALMA Band6 forms near Si IV heights, in upper chromosphere of dynamic features | **supported**
- H: Higher previous correlations come from plage definition | E: Include periphery pixels in the plage sample | R: C.C. rises from 0.56 to 0.74 | F: Plage selection biases correlations | **partially**
- H: ALMA shows shock heating in plage | E: Tb time series against λ-t plots | R: 10-20% Tb jumps from 7,500 K, decays 60-120 s | F: Indications of shock heating | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Model should not be taken as perfect; modeled Band6 Tb is 2,000 K lower than observed  
  > "the distribution of modeled brightness temperatures of *ALMA*/Band6 is lower by 2,000 K as compared to the observations." (6 Summary & Conclusions)
- Caveat (inferred, ours): Single dataset and region
- Caveat (inferred, ours): Photospheric-defined masks may offset from chromospheric plage
- Caveat (inferred, ours): Shock analysis in one 1"x1" region with data gaps
- Caveat (inferred, ours): No uncertainties on C.C.

## Reproducibility

- Data public (paper): ALMA project 2016.1.00050.S acknowledged  
  > "This paper makes use of the following *ALMA* data: ADS/JAO.ALMA#2016.1.00050.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Paper I reduction details
- Missing: Bifrost simulation data
- Data volume (inferred): tens to hundreds of GB (ALMA mosaic time series plus IRIS)
- Score (inferred): 4/5, Data public, but processing delegated to Paper I and simulation needed for part of the results.
- Rediscovery candidate: no, Recipe depends on Paper I and Bifrost data not described here.

## Links

- Method: Paper I; Chintzoglou et al 2020a (Data reduction and spicule analysis)
- Method: (cite: Martinez-Sykora_etal_2020b) (Bifrost simulation)
- Companion: Chintzoglou et al 2020a (Paper I) (Spicule evolution from the same dataset)
- Related: Bastian et al. 2017, 2018
- Related: Jafarzadeh et al. 2019

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
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
  "facts": 68,
  "stated": 27,
  "rate": 0.397
 },
 "evidence_ok": true
}
```
