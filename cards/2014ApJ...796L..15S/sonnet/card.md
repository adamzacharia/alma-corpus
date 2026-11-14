# Around the Ring We Go: The Cold, Dense Ring of Molecular Gas in NGC 1614

`2014ApJ...796L..15S` | The Astrophysical Journal Letters 2014 | first author: Sliwa, Kazimierz | arXiv: 1410.6982 | DOI: 10.1088/2041-8205/796/1/L15

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies
- Question: What are the physical conditions of the molecular gas in the circumnuclear ring of the LIRG NGC 1614, including the 12CO/13CO abundance ratio and alpha_CO?  
  > "to constrain the physical conditions of the molecular gas at a resolution of 230 pc using a radiative transfer code and a Bayesian likelihood analysis." (abstract)
- Target **NGC 1614**: coordinates _not stated_; z/distance D_L = 67.9 Mpc; 1'' = 330 pc  
  > "NGC 1614 ($D_{L}$ = 67.9 Mpc; 1$''$ = 330 pc)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00182.S, 2011.0.00768.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: each sideband roughly 4 GHz  
  > "Each sideband is roughly 4GHz in width." (2.3 ALMA)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ALMA CO 3-2 0.7x0.4 arcsec; CO 6-5 0.4x0.3; HCO+ 4-3 0.6x0.4; continuum 0.3x0.2  
  > "| $^{12}$CO $J$=6-5  | ALMA | 920 $\pm$ 10 | 0.4 x 0.3 | 7 |  |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: rms 3 mJy/beam (CO 3-2), 7 (CO 6-5), 0.9 (HCO+), 1.4 (continuum) per 20 km/s channels  
  > "| $^{12}$CO $J$=3-2  | ALMA | 1680 $\pm$ 10 | 0.7 x 0.4 | 3 |  |" (Table 1)
- time on source: _not stated_
- observing dates: ALMA Cycle 0  
  > "NGC 1614 was observed in $^{12}$CO $J$=3-2 and $^{12}$CO $J$=6-5 using ALMA during Cycle 0." (2.3 ALMA)
- pi or archival as stated: archival, unpublished  
  > "we present unpublished archival ALMA and new CARMA CO observations for NGC 1614." (Introduction)
- Line: 12CO J=3-2 (not stated)
- Line: 12CO J=6-5 (not stated)
- Line: HCO+ J=4-3 (not stated)
- Other facility **CARMA**: new 12CO and 13CO J=1-0 (C and D arrays)  
  > "in $^{12}$CO and $^{13}$CO $J$=1-0, simultaneously." (2.1 CARMA)
- Other facility **SMA**: 12CO and 13CO J=2-1 and 12CO J=3-2 maps  
  > "We combined data from all three configurations to obtain high-resolution maps of $^{12}$CO and $^{13}$CO $J$=2-1." (2.2 SMA)
- Other facility **JCMT**: short-spacing CO 2-1 and 3-2 maps  
  > "To recover the short spacings of the SMA $^{12}$CO $J$=2-1 and $J$=3-2 maps, we used the James Clerk Maxwell Telescope (JCMT)" (2.2 SMA)
- Other facility **Herschel FTS**: total CO 6-5 flux 1320 +/- 40 Jy km/s  
  > "we measure a total $^{12}$CO $J$=6-5 flux of 1320 $\pm$ 40 Jy km s$^{-1}$ from the Herschel FTS spectrum of NGC 1614." (3 Morphology)
- External data: Previously published SMA CO 2-1 / 13CO data, very-extended configuration calibrated data  
  > "We obtained the raw data for the extended observations and the calibrated data for the very-extended observations from the SMA archive." (2.2 SMA) [from König et al. 2013 (cite: Konig2013)]
- External data: CO-to-H2 abundance ratio x_CO = 3e-4  
  > "is the CO-to-H$_{2}$ abundance ratio assumed to be 3 $\times$ 10$^{-4}$ (Ward et al. 2003)" (5 CO-to-H2 Conversion Factor) [from Ward et al. 2003]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: calibrated uv-datasets from ALMA archive  
  > "We use the calibrated $uv$-datasets obtained from the ALMA archive." (2.3 ALMA)
- flux calibrator: _not stated_
- flux scale uncertainty: 20% assumed  
  > "this is within our assumed calibration uncertainty of 20$\%$." (2.3 ALMA)
- self calibration: two rounds of phase-only self-calibration using 12CO line emission  
  > "We performed two rounds of phase-only self-calibration on both datasets using the $^{12}$CO line emission." (2.3 ALMA)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: using line-free channels, in CASA  
  > "All datasets have been continuum subtracted using line-free channels and imported into CASA for further processing and imaging." (2 Observations)
- line free channels: _not stated_
- primary beam correction: applied to integrated intensity maps  
  > "all integrated intensity maps have been primary beam corrected." (2 Observations)
- array combination: CO 3-2 ALMA imaged with SMA+JCMT short-spacing datacube as starting model  
  > "we use the SMA short-spacings recovered $^{12}$CO $J$=3-2 datacube as a starting model so as to better constrain the shorter baselines." (2.3 ALMA)
- smoothing: angular resolutions matched for line ratio maps  
  > "We match the angular resolutions of the two maps used to create the individual line ratio maps (Figure 2)." (2.4 Line Ratios)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Bayesian likelihood code  
  > "For more details on the likelihood code, see Kamenetzky et al. (2012)." (4 Molecular Gas Physical Conditions) [from Kamenetzky et al. (2012)]
- three priors  
  > "We also implemented the three priors described in Sliwa et al. (2013)." (4 Molecular Gas Physical Conditions) [from Sliwa et al. (2013)]
- feathering of JCMT and SMA  
  > "We combined the JCMT and SMA data using the “feathering" method as described in Sliwa et al. (2012)." (2.2 SMA) [from Sliwa et al. (2012)]

### Not stated but needed to reproduce (our reading)

- CASA version and imaging parameters (weighting, robust, cell, size, deconvolver, masks)
- line-free channels and channels used for integrated intensity
- self-calibration solution intervals and reference
- the three priors' forms
- how fluxes at positions were extracted and uncertainties assigned
- dynamical mass formula and line width/size measurement

## Analysis recipe

1. **Image ALMA data**: Self-calibrate, continuum-subtract and image calibrated archival data in CASA; make 20 km/s cubes and integrated intensity maps  
  > "We created datacubes with 20 km s$^{-1}$ and 100 km s$^{-1}$ channel widths for $^{12}$CO and $^{13}$CO, respectively." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: ALMA CO 3-2 and SMA flux scales differ ~10%, within 20% uncertainty  
  > "The flux scales of the two datasets differ by roughly 10$\%$" (2.3 ALMA)
2. **Line ratio maps**: Ratio maps at matched resolution with 3 sigma cutoff (1 sigma for 13CO 2-1)  
  > "We implemented a 3$\sigma$ cutoff on each map except $^{13}$CO $J$=2-1, where a 1$\sigma$ cutoff was used." (2.4 Line Ratios)
   - fitting: _not stated_
   - validation: _not stated_
3. **RADEX grid + Bayesian likelihood at five ring positions**: RADEX grids of Tkin, nH2, N(12CO), filling factor, and [12CO]/[13CO]; likelihood gives 1DMax and 4DMax at 0.7x0.6 arcsec  
  > "The 4DMax is the maximum likelihood of a single grid point based on the four-dimensional distribution of the parameters that comprise the grid." (4 Molecular Gas Physical Conditions)
   - software: RADEX
   - parameter: Tkin 10^0.7-10^3.8 K (71 pts); nH2 10^1-10^7 (71); N 10^12-10^22 (81); filling factor 10^-5-1 (71); abundance ratio 10-10^5 (51)  
  > "abundance ratios (\[$^{12}$CO\]/\[$^{13}$CO\]; range=10-10$^{5}$, 51 points)" (4 Molecular Gas Physical Conditions)
   - assumption: adopted ratios r21 = 0.93±0.23, 13r21 = 2.0±0.6, R21 = 20±3 to estimate CO 1-0, 13CO 1-0 and 13CO 2-1 fluxes  
  > "$r_{21}$ = 0.93 $\pm$ 0.23, $^{13}r_{21}$ = 2.0 $\pm$ 0.6, and $R_{21}$ = 20 $\pm$ 3." (4 Molecular Gas Physical Conditions)
   - fitting: Bayesian likelihood on grid with three priors  
  > "we use a Bayesian likelihood code to create probability distributions for the various parameters." (4 Molecular Gas Physical Conditions)
   - validation: hole refit excluding CO 6-5 after single component fails  
  > "We re-model the molecular gas of the “hole" excluding the $^{12}$CO $J$=6-5 flux." (4 Molecular Gas Physical Conditions)
4. **Derive alpha_CO and x_CO limits**: alpha_CO from 4DMax column density, beam area and r21-scaled CO 2-1 luminosity; dynamical-mass alpha_CO from CO 3-2 line width and size  
  > "We measure $M_{dyn}$ using the line width and the source size, both measured using the $^{12}$CO $J$=3-2 map." (5 CO-to-H2 Conversion Factor)
   - assumption: x_CO = 3e-4  
  > "is the CO-to-H$_{2}$ abundance ratio assumed to be 3 $\times$ 10$^{-4}$ (Ward et al. 2003)" (5 CO-to-H2 Conversion Factor)
   - fitting: _not stated_
   - validation: compared with dynamical alpha_CO  
  > "We then use $M_{dyn}$ and the CO luminosity within the region to measure $\alpha_{CO, dyn}$ (=$M_{dyn}$/L$_{CO}$)." (CO-to-H$_{2}$ Conversion Factor)

## Software

- **CASA** : calibration, imaging  
  > "imported into CASA for further processing and imaging." (2 Observations)
- **RADEX** : radiative transfer grids  
  > "we use the radiative transfer code RADEX (van der Tak et al. 2007)." (4 Molecular Gas Physical Conditions)
- **Starlink** : JCMT data reduction  
  > "using the `Starlink` software (Currie et al. 2008)." (2.2 SMA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Tkin around ring | 20-40 | not stated | K | 3 | the molecular gas is cold (20-40 K) and dense ($>$ 10$^{3.0}$ cm$^{-3}$) |
| [12CO]/[13CO] | >130 | not stated | dimensionless | 3 | The $^{12}$CO-to-$^{13}$CO abundance ratio is found to be greater than 130 |
| alpha_CO ring | 0.9-1.5 | not stated | Msun (K km/s pc^2)^-1 | 4 | to range from 0.9 to 1.5 $M_{\odot}$ |
| ALMA CO 6-5 flux missing | ~30 | not stated | percent | 1 | This shows that the ALMA map is missing roughly 30$\%$ of the $^{12}$CO $J$=6-5 flux |
| alpha_CO,dyn east, west, south | 3.5, 2.6, 2.4 | not stated | Msun (K km/s pc^2)^-1 | 4 | we measure $\alpha_{CO,dyn}$ to be 3.5, 2.6 and 2.4 |

## Qualitative findings

- Only the hole needs a second warmer component.  
  > "only the “hole" shows evidence of a second warmer molecular gas component" (4 Molecular Gas Physical Conditions)

## Claim tuples

- H: Ring gas conditions | E: RADEX + Bayesian analysis at five positions | R: Tkin 20-40 K, n>10^3 | F: Ring gas is cold and dense | **supported**
- H: Is [12CO]/[13CO] elevated? | E: Likelihood fits | R: >130 around ring | F: Over twice local ISM value | **supported**
- H: alpha_CO is below Galactic | E: Column-density method and dynamical mass | R: 0.9-1.5 | F: ULIRG-like value should be used | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): x_CO is the biggest uncertainty; may not apply to the hole  
  > "The biggest uncertainty in measuring $\alpha_{CO}$ is the assumed value of $x_{\rm{CO}}$." (5 CO-to-H2 Conversion Factor)
- Caveat (inferred, ours): Ratios, not measured lines, used for CO 1-0 and 13CO fluxes
- Caveat (inferred, ours): Only five positions, no multi-component fit
- Caveat (inferred, ours): Missing flux in ALMA CO 6-5 not corrected

## Reproducibility

- Data public (paper): ALMA data from archive  
  > "We use the calibrated $uv$-datasets obtained from the ALMA archive." (2.3 ALMA)
- Products in archive: _not stated_
- Missing: imaging parameters
- Missing: likelihood code and priors details
- Missing: CARMA data access
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Public data but sparse imaging details and reliance on external likelihood code.
- Rediscovery candidate: no, Recipe incomplete; relies on unreleased code and multi-facility data.

## Links

- Method: Kamenetzky et al. (2012) (likelihood code)
- Method: Sliwa et al. (2013) (priors)
- Companion: König et al. 2013 (SMA CO 2-1 observations)

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 40,
  "rate": 0.556
 },
 "evidence_ok": true
}
```
