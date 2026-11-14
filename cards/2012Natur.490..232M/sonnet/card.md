# Unexpectedly large mass loss during the thermal pulse cycle of the red giant star R Sculptoris

`2012Natur.490..232M` | Nature 2012 | first author: Maercker, M. | arXiv: 1210.3030 | DOI: 10.1038/nature11511

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What are the timescales and mass-loss properties during and after a thermal pulse of the AGB star R Sculptoris, as revealed by the CO(3-2) detached shell and spiral structure?  
  > "It has hitherto been impossible to constrain observationally the timescales and mass-loss properties during and after a thermal pulse" (abstract)
- Target **R Sculptoris**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00131.S
- bands: CO(J=3-2) at 345 GHz, Cycle 0  
  > "The detached shell around R Sculptoris was observed in CO( _J_ = 3 − 2) emission at 345 GHz using the Atacama Large Millimeter/submillimeter Array (ALMA) during Cycle 0 operations" (main text)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Cycle 0 compact configuration  
  > "using the ALMA Cycle 0 compact configuration specifications" (Figure 4 caption)
- baselines: _not stated_
- angular resolution: 1.3"  
  > "with an angular resolution of 1.3”" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (345 GHz)
- External data: Present-day expansion velocity and mass-loss rate (3e-7 Msun/yr) of R Scl wind  
  > "The present-day mass-loss rate is estimated to be 3×10 [−] [7] M `!` yr [−] [1] [,] [3]" (main text) [from Schöier, Lindqvist & Olofsson 2005 (ref 3)]
- Simulation/model as data: Modified GADGET-2 SPH models of the binary wind with radiative cooling, post-processed with LIME and CASA simdata  
  > "we modeled the system with a modified version of the GADGET-2 SPH code [14], including detailed radiative cooling [15] ." (main text)

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
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Calibration and imaging procedures (CASA version, weighting, cleaning), in supplementary information not provided
- Distance to R Scl
- SPH model parameters (masses, separation, particle numbers)
- Gas-mass and CO abundance assumptions for mass-loss rates
- LIME setup

## Analysis recipe

1. **trace spiral in position angle vs radius**: Linear fits to emission peaks in p.a. vs radius diagram of the systemic-velocity image, converted to wind velocity evolution assuming 350 yr orbital period  
  > "The linear fits can hence be translated directly into a velocity evolution (Fig. 3)." (Figure 2 caption)
   - assumption: Orbital period 350 yr from present-day expansion velocity 10.5 km/s  
  > "The present-day expansion velocity is estimated to be 10.5 km s [!1], giving a binary period of 350 years." (Figure 2 caption)
   - fitting: _not stated_
   - validation: _not stated_
2. **SPH and radiative transfer modelling**: SPH binary wind model with derived velocity and mass-loss profiles as input, LIME radiative transfer, simdata, compared to observed image  
  > "The modeled density, temperature, and velocity structures of the SPH model are then used as input in the 3-dimensional radiative transfer code LIME [16] ." (main text)
   - software: GADGET-2, LIME, CASA simdata
   - assumption: Inclination 90 deg; inter-pulse time 50,000 yr  
  > "The inclination angle of the binary system to the line of sight is 90 [o] ." (Figure 4 caption)
   - fitting: _not stated_
   - validation: Model brightness distribution compared visually with observed intensities  
  > "the brightness distribution reproduces the observed intensities well (Fig. 4)" (main text)

## Software

- **GADGET-2** : SPH modelling of the binary wind  
  > "modified version of the GADGET-2 SPH code [14]" (main text)
- **LIME** : 3D radiative transfer of the SPH model  
  > "3-dimensional radiative transfer code LIME [16]" (main text)
- **CASA** : simdata to simulate ALMA observations of the model  
  > "processed by _simdata_ in _CASA_" (Figure 4 caption)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Detached shell radius | 18.5 | not stated | arcsec | 0 | shell radius of _R_ sh = 18.5” |
| Shell expansion velocity | 14.3 | not stated | km/s | 0 | shell expansion velocity of _v_ sh = 14.3 km s [−] [1] |
| Spiral winding spacing | 2.6 | 0.07 | arcsec | 1 | constant separation of 2.6”±0.07” |
| Binary period | 350 | not stated | yr | 1 | giving a binary period of 350 years |
| Total gas mass in shell | 2.5e-3 | not stated | Msun | 0 | An estimated total gas-mass in the shell of 2.5×10 [−] [3] M `!` |

## Qualitative findings

- Spiral structure connects the central star to the detached shell, implying a binary companion  
  > "we conclude that R Sculptoris is a binary system that underwent a thermal pulse ≈ 1800 years ago, lasting ≈ 200 years." (abstract)

## Claim tuples

- H: Does R Scl host a binary companion that shapes the wind? | E: ALMA CO(3-2) imaging plus SPH and LIME modelling | R: Spiral of ~5 windings with spacing 2.6" reproduced by the binary SPH model | F: R Scl is a binary that had a thermal pulse ~1800 yr ago lasting ~200 yr | **supported**
- H: How much mass is lost during the pulse? | E: Shell mass and CO intensity ratios, SPH modelling | R: Pulse mass-loss rate 7e-6 to 2.5e-5 Msun/yr, ~30 times the pre-pulse rate | F: About 3 times more mass is returned to the ISM than previously thought | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Intensity contrast between spiral windings and interwinding material indicates a more complicated mass-loss-rate variation than modelled  
  > "variations in the intensity contrast between the spiral windings and interwinding material indicate a more complicated mass-loss-rate variation." (Figure 4 caption)
- Caveat (inferred, ours): Binary companion not directly detected
- Caveat (inferred, ours): Model is not uniquely fitted, no formal parameter search or uncertainties
- Caveat (inferred, ours): Mass-loss rates depend on unstated CO abundance and distance

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Supplementary information with data reduction and model details
- Missing: SPH model parameters
- Data volume (inferred): ~10-50 GB (Cycle 0 single-field band 7 data)
- Score (inferred): 3/5, Data are public, but the main text omits reduction and modelling details.
- Rediscovery candidate: no, Key recipe details are in unavailable supplementary information and the results rely on custom SPH modelling.

## Links

- Method: Brinch & Hogerheijde 2010 (ref 16) (LIME radiative transfer)
- Method: Springel 2005 (ref 14) (GADGET-2 SPH code)
- Companion: Schöier, Lindqvist & Olofsson 2005 (ref 3) (Present-day wind properties of R Scl)

## Checks

```json
{
 "quotes": 26,
 "quotes_ok": 26,
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
  "facts": 58,
  "stated": 16,
  "rate": 0.276
 },
 "evidence_ok": true
}
```
