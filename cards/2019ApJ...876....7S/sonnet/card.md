# An Analytical Model of Radial Dust Trapping in Protoplanetary Disks

`2019ApJ...876....7S` | The Astrophysical Journal 2019 | first author: Sierra, Anibal | arXiv: 1903.08769 | DOI: 10.3847/1538-4357/ab1265

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: How do dust grains of different sizes concentrate in axisymmetric gas pressure maxima, and can an analytic dust-trapping model fit the multiwavelength mm emission of HD 169142 to give the dust-to-gas ratio and alpha?  
  > "We study dust concentration in axisymmetric gas rings in protoplanetary disks." (abstract)
- Target **HD 169142**: coordinates _not stated_; z/distance 117 ± 4 pc  
  > "at a distance of d = 117 ± 4 pc (Gaia Collaboration et al. 2016)." (4.1. HD 169142); "with an inclination angle of ∼ 14deg (cos i = 0.974), and with its" (4.1. HD 169142); distance from Gaia Collaboration et al. 2016  
  > "at a distance of d = 117 ± 4 pc (Gaia Collaboration et al. 2016)." (4.1. HD 169142); "with an inclination angle of ∼ 14deg (cos i = 0.974), and with its" (4.1. HD 169142)

## Data provenance

- ALMA projects: 2012.1.00799.S, 2013.1.00592.S, 2016.1.01158.S
- bands: Band 7 (0.87 mm), Band 6 (1.3 mm), Band 3 (3.0 mm) continuum; Band 6 CO lines  
  > "dust 7 0.87 330 Briggs; robust=0.5 0.19 × 0.12; 84.97 170 196" (Table C1)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Dust maps convolved to 0.20 arcsec circular beam (23.4 AU); gas maps 0.16 arcsec (18.7 AU)  
  > "All the dust maps were convolved to the same circular beam of 0.20 arc sec, while the gas maps have a circular beam of 0.16 arcsec." (4.1. HD 169142)
- max recoverable scale: _not stated_
- sensitivity: rms (convolved): 196 uJy/beam (0.87 mm), 91 (1.3 mm), 23 (3.0 mm)  
  > "dust 3 3.0 100 Briggs; robust=-1 0.17 × 0.07;-89.22 25 23" (Table C1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival data from 2012.1.00799.S (0.87 mm), Fedele et al. 2017 (1.3 mm and CO), Macias et al. in prep. (3 mm)  
  > "archival data from program 2012.1.00799.S, Fedele et al. 2017, and Macias et al. in prep. respectively" (4.1. HD 169142)
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Other facility **VLA**: 7 mm imaging used for context  
  > "The dust thermal emission of the disk was first imaged with the VLA at 7 mm" (4.1. HD 169142)
- External data: Disk mass M_disk = 0.019 Msun used to normalize gas surface density  
  > "For a disk mass of M disk = 0.019 M ⊙ (Fedele et al. 2017)" (4.2 Gas surface density) [from Fedele et al. 2017]
- External data: Stellar parameters: M*=1.65 Msun, T*=8100 K, R*=2.2 Rsun; inclination 14 deg, PA 5 deg  
  > "a mass of M ∗ = 1.65 M ⊙ (Blondel & Djie 2006) with an effective temperature T ∗ = 8100 K" (4.1. HD 169142) [from Blondel & Djie 2006; Osorio et al. 2014; Raman et al. 2006]
- External data: Dust composition abundances (silicates, organics, ice)  
  > "for a dust composition of silicates, organics, and ice with the relative abundances described by Pollack et al. (1994)" (4.3 Dust properties) [from Pollack et al. (1994)]
- Simulation/model as data: 3D non-ideal MHD simulation of dust in a disk (Flock et al. 2015, Ruge et al. 2016), snapshot at 400 inner orbits, used to test the analytic model  
  > "We choose a snapshot of the simulation at a time of 400 inner orbits of the disk." (3. Application to numerical simulation)

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

- task: CASA (v 4.7.0) continuum imaging  
  > "Continuum images were created using CASA (v 4.7.0)" (C. Imaging parameters)
- deconvolver: _not stated_
- weighting robust: Band 7 Briggs robust=0.5; Band 6 natural; Band 3 Briggs robust=-1; CO natural  
  > "dust 6 1.3 230 Natural weighting 0.19 × 0.13; 63.42 100 91" (Table C1)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Dust images convolved to common 0.20 arcsec circular beam  
  > "All dust continuum images were finally convolved to the same circular beam of 0.20 arcsec." (Table C1)
- final beam: _not stated_
- final rms: 196, 91, 23 uJy/beam at 0.87, 1.3, 3.0 mm  
  > "dust 7 0.87 330 Briggs; robust=0.5 0.19 × 0.12; 84.97 170 196" (Table C1)

### Inherited from earlier work

- Opacity and albedo curves for the dust size distributions  
  > "The opacity and albedo curves as a function of the wavelength for different dust size distributions are shown in Figures 9 and 10 of Sierra et al. (2017)." (4.3 Dust properties) [from Sierra et al. (2017)]
- Opacities computed with the DA01 code  
  > "are computed with the code of (DA01) for a dust composition of silicates, organics, and ice" (4.3 Dust properties) [from D'Alessio et al. 2001]

### Not stated but needed to reproduce (our reading)

- Calibration details and pipeline version for the archival data
- Calibration of the 3 mm data (Macias et al. in prep.) and its project code assignment
- Line-free channels and continuum subtraction for the CO maps
- Line width and moment-map parameters for the 13CO column density
- Dust material density rho_m
- Ring-by-ring annuli and radial binning for the profiles
- Image size and cell size
- Flux calibration uncertainty

## Analysis recipe

1. **Derive gas surface density and excitation temperature**: 12CO optically thick and 13CO optically thin; compute 13CO column density and optical depth, convert to H2 with abundance normalized to total disk mass  
  > "We use the J : 2 → 1 lines and assume that 12CO is optically thick and the 13CO is optically thin." (4.2 Gas surface density)
   - software: CASA
   - parameter: M_disk = 0.019 Msun gives [13CO/H2] = 1.0e-5  
  > "the abundance between the 13CO and the H 2 molecules of [ 13CO/H 2 ] = 1.0 × 10 −5" (4.2 Gas surface density)
   - assumption: 12CO optically thick, 13CO optically thin  
  > "We use the J : 2 → 1 lines and assume that 12CO is optically thick and the 13CO is optically thin." (4.2 Gas surface density)
   - fitting: _not stated_
   - validation: 13CO tau < 0.8 throughout the disk  
  > "We find that τ 0 13 < 0.8 throughout the disk." (4.2 Gas surface density)
2. **Derive spectral index beta and maximum grain size a_max(r)**: Fit the radiative transfer solution (scattering, non-Rayleigh-Jeans) to the three intensity profiles to get beta(r), then map to a_max for assumed p using DA01 opacities  
  > "derived from the dust continuum observations following the latter procedure, without assuming optically thin emission nor the Rayleigh-Jeans approximation, and including the mass scattering opacity." (4.3 Dust properties)
   - software: DA01 opacity code
   - parameter: p = 3.5, a_min = 0.05 um; inner/outer dust radius 15 and 90 AU  
  > "the inner and outer dust radius are set to be 15 AU and 90 AU respectively." (4.3 Dust properties)
   - assumption: Power-law dust temperature T0=500 K at 1 AU, q=1/2  
  > "where T 0 = 500 K at ϖ 0 = 1 AU and q = 1/2." (4.3 Dust properties)
   - assumption: Vertically isothermal slab with MI93 mean intensity  
  > "We approximate J ν by the analytical solution found by Miyake & Nakagawa (1993)" (4.3 Dust properties)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit eps_global and alpha on a model grid**: Grid of 50x50 log-spaced models; compare model and observed azimuthally averaged intensity profiles via reduced chi-squared at each wavelength; average best values  
  > "The number of models for each parameter is 50 (the total number of models is 50 × 50) and the values are logarithmically equally spaced." (4.4 Best fit dust model)
   - parameter: alpha 1e-5 to 1e-1; eps_global 1e-4 to 1e-1  
  > "α from 10 −5 to 10 −1 , while ϵ global varies from 10 −4 to 10 −1 ." (4.4 Best fit dust model)
   - assumption: Uncertainty sigma = RMS/sqrt(n beams in ring); model convolved to observed beam  
  > "σ λ obs ( ϖ ) = RMS λ / √ n ," (4.4 Best fit dust model)
   - fitting: Grid search minimizing reduced chi-squared (no sampler)  
  > "We choose the parameters that minimize the reduced chi-squared of the dust continuum emission of the observed dust maps and the emission of a grid of models." (4. Application of the model to HD 169142)
   - validation: Compare model and observed maps and residuals; isocontours at 1.5 times minimum chi2  
  > "Figure (8) plots the isocontours where the value of the reduced chi-squared is 1.5 times the minimum value" (4.4 Best fit dust model)

## Software

- **CASA** 4.7.0: Continuum imaging of ALMA data  
  > "Continuum images were created using CASA (v 4.7.0)" (C. Imaging parameters)
- **DA01 opacity code (D'Alessio et al. 2001)** : Dust opacities and albedo  
  > "are computed with the code of (DA01)" (4.3 Dust properties)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Global dust-to-gas ratio, HD 169142 | 1.05e-2 | not stated | dimensionless | 3 | ϵ global = 1.05 × 10 − 2 and α = 1.35 × 10 − 2 |
| Viscosity coefficient alpha, HD 169142 | 1.35e-2 | not stated | dimensionless | 3 | ϵ global = 1.05 × 10 − 2 and α = 1.35 × 10 − 2 |
| Total dust mass | 2.0e-4 | not stated | Msun | 3 | this means that the total dust mass is 2.0 × 10 − 4 M ⊙ . |
| Best alpha in simulation test | 1.3e-3 | not stated | dimensionless | 0 | The minimum is obtained for α b = 1.3 × 10 − 3 |
| [13CO/H2] abundance | 1.0e-5 | not stated | dimensionless | 1 | [ 13CO/H 2 ] = 1.0 × 10 − 5 |
| Local dust-to-gas enhancement in first maximum | factor of 6 | not stated | dimensionless | 3 | The local dust to-gas mass ratio in the first maximum increases by a factor of 6 compared with the global dust-to-gas mass ratio |

## Qualitative findings

- Maximum grain size is >10 cm at the inner ring (~27 AU) and decreases to ~2 mm at 90 AU  
  > "The maximum dust size in the center of the inner ring ( ∼ 27 AU) is a max > 10 cm." (6. Conclusions)

## Claim tuples

- H: An analytic steady-state drag-diffusion dust model reproduces dust concentration in a simulated gas ring | E: Compared model with 3D MHD simulation ring, fitting alpha by minimizing sigma^2 | R: Best alpha = 1.3e-3; model profile widths match simulation for three grain sizes | F: Model reproduces size-dependent dust concentration | **supported**
- H: The model can explain HD 169142 multiwavelength mm emission with common parameters | E: Grid fit to 0.87, 1.3, 3.0 mm profiles | R: eps_global=1.05e-2, alpha=1.35e-2 | F: Parameters simultaneously explain the profiles | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Fitted alpha depends on the resolution of the gas structure; non-axisymmetric structures not modelled  
  > "Note that the fitted value of α depends on the resolution of the gas structure." (4.4 Best fit dust model)
- Caveat (inferred, ours): Fit has strong degeneracy among a_max, p, alpha and opacity assumptions
- Caveat (inferred, ours): No parameter uncertainties given
- Caveat (inferred, ours): Gas density depends on assumed disk mass and 13CO/H2
- Caveat (inferred, ours): Best alpha differs between wavelengths and values are averaged

## Reproducibility

- Data public (paper): Archival ALMA programs listed; 3 mm data cited as in prep.  
  > "archival data from program 2012.1.00799.S, Fedele et al. 2017, and Macias et al. in prep. respectively" (4.1. HD 169142)
- Products in archive: _not stated_
- Missing: Calibration and imaging details (image size, cell, masks)
- Missing: Exact project-to-band mapping
- Missing: Dust material density
- Missing: Radial binning of intensity profiles
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Analytic model fully given with equations and grid; data are archival, but imaging details and some data provenance are incomplete.
- Rediscovery candidate: no, Observational data partly unpublished (in prep.) and imaging recipes incomplete.

## Links

- Method: D'Alessio et al. 2001 (Opacity code)
- Method: Miyake & Nakagawa 1993 (Radiative transfer source function)
- Companion: Fedele et al. 2017 (Source of 1.3 mm continuum and CO data)
- Companion: Sierra et al. 2017 (Vortex dust model, opacities)

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 36,
  "rate": 0.514
 },
 "evidence_ok": true
}
```
