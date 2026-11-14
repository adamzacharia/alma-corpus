# Meridional flows in the disk around a young star

`2019Natur.574..378T` | Nature 2019 | first author: Teague, Richard | arXiv: 1910.06980 | DOI: 10.1038/s41586-019-1642-0

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: What are the three-dimensional gas velocity components (v_phi, v_R, v_Z) in the upper layers of the HD 163296 disk, and do they show meridional flows at the gap locations?  
  > "Here we present the radial profiles of the three velocity components of gas in upper disk layers in the disk of HD 163296 as traced by $^{12}$CO molecular emission." (abstract)
- Target **HD 163296**: coordinates _not stated_; z/distance 101 pc  
  > "corresponding to $10.5~{\rm au} \times 9.6~{\rm au}$ at the source distance of 101 pc" (Observations); distance from Bailer-Jones et al. 2018 (Gaia)  
  > "corresponding to $10.5~{\rm au} \times 9.6~{\rm au}$ at the source distance of 101 pc" (Observations)

## Data provenance

- ALMA projects: 2013.1.00366.S, 2013.1.00601.S, 2016.1.00484.L
- bands: _not stated_
- frequencies and spectral setup: spectral resolution 640 m/s after Hanning smoothing  
  > "a spectral resolution of ${640}~{\rm m\,s^{-1}}$ after Hanning smoothing" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.104'' x 0.095'' (10.5 au x 9.6 au)  
  > "a spatial resolution of $0.104\ensuremath{''} \times 0.095\ensuremath{''}$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Public DSHARP images combining three projects  
  > "Combining data from three projects" (Observations)
- Line: 12CO J=2-1 (not stated)
- External data: Disk inclination 46.7 +/- 0.1 deg and PA 133.3 deg from continuum ring fits  
  > "we adopt the inclination and position angle found from continuum(cite: Isella_ea_2018), $i = 46.7\ensuremath{^\circ}$" (Deriving an Emission Surface) [from Isella et al. 2018]
- External data: Distance 101 pc  
  > "assuming a source distance of 101 pc(cite: Bailer-Jones_ea_2018)" (Deriving an Emission Surface) [from Bailer-Jones et al. 2018]
- Simulation/model as data: FARGO3D 3D isothermal hydrodynamic simulation with planets of 0.5, 1, 2 MJup at 87, 140, 237 au  
  > "We add 0.5 Jupiter-mass planet at 87 au, 1 Jupiter-mass planet at 140 au, and 2 Jupiter-mass planet 237 au." (Hydrodynamic Simulation Setup)

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
- cell size: pixel scaling 13 mas  
  > "(the pixel scaling was 13 mas)" (Measuring the Velocity Structure)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Hanning smoothing  
  > "a spectral resolution of ${640}~{\rm m\,s^{-1}}$ after Hanning smoothing" (Observations)
- final beam: 0.104'' x 0.095''  
  > "a spatial resolution of $0.104\ensuremath{''} \times 0.095\ensuremath{''}$" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Data reduction and imaging procedure  
  > "More details about the data reduction and imaging procedure can be found in Isella et al. (2018)." (Observations) [from Isella et al. (2018)]
- Velocity inference method (rotation and radial velocities from stacked spectra)  
  > "we follow the method outlined in Teague et al. (2018a,b)(cite: Teague_ea_2018a; Teague_ea_2018b)" (Measuring the Velocity Structure) [from Teague et al. 2018a,b]
- Non-parametric emission surface method  
  > "The second method follows the method presented in Pinte et al. (2018a)" (Deriving an Emission Surface) [from Pinte et al. 2018a]
- Disk model for the simulation  
  > "We adopt a parametric disk model similar to the one presented in Flaherty et al. (2017)" (Hydrodynamic Simulation Setup) [from Flaherty et al. 2017]

### Not stated but needed to reproduce (our reading)

- Exact DSHARP image product (file name, robust weighting) of the 12CO cube
- Choice of Delta V for the line-core fit
- Radial range and number of annuli used, and the polynomial fitting range
- Emission-surface parameters for gas-temperature and sound-speed conversion beyond the description
- FARGO3D setup details such as boundary conditions and the smoothing of the planet potential

## Analysis recipe

1. **Map line centres**: Fit a quadratic to the peak pixel and its two neighbours to get line-centre maps  
  > "which fits a quadratic curve to the pixel of peak intensity and the two neighbouring pixels" (Deriving an Emission Surface)
   - software: bettermoments
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit the parametric emission surface**: Fit the Keplerian map with a two-power-law emission surface and 10 free parameters  
  > "leaving 10 free parameters for the model." (Deriving an Emission Surface)
   - software: eddy
   - parameter: Only pixels at least a beam FWHM apart are used in the likelihood  
  > "Only spatially independent pixels, those at least a beam FWHM apart, were considered in the calculation of the likelihood." (Deriving an Emission Surface)
   - assumption: Distance 101 pc; inclination prior 46.7 +/- 0.1 deg  
  > "Flat priors were assumed for all values except the inclination which has a prior of $i = 46.7\ensuremath{^\circ} \pm 0.1\ensuremath{^\circ}$" (Deriving an Emission Surface)
   - fitting: MCMC with 64 walkers, 10,000 burn-in steps and 10,000 sampling steps, flat priors  
  > "64 walkers were run for 10,000 steps for an initial burn-in period, before an additional 10,000 steps were used to sample the posterior distributions." (Deriving an Emission Surface)
   - validation: Compared with a non-parametric surface and with a fit that fixes Z1 = 0  
  > "Fixing $Z_1 = 0$ results in a comparable geometric parameters" (Deriving an Emission Surface)
3. **Non-parametric emission surface**: Pinte et al. 2018a method with a Gaussian Process on the raw points  
  > "the raw data points were modelled with a Gaussian Process resulting in a smooth emission surface, rather than radially binning the data." (Deriving an Emission Surface)
   - assumption: Circular orbits; i = 46.7 deg, PA = 133.3 deg  
  > "This method assumes that the gas is on circular orbits" (Deriving an Emission Surface)
   - fitting: _not stated_
   - validation: Compared with the parametric surface; consistent for r < 3''  
  > "Using only the data points for $r < 3\ensuremath{''}$ we find a consistent non-parametric emission surface." (Deriving an Emission Surface)
4. **Measure v_phi and v_R in annuli**: Annuli 25 mas wide; random independent pixels; maximise the Gaussian Process likelihood of the shifted and stacked spectra; 20 realisations per annulus  
  > "For each annulus, 20 different realisations with different pixels were performed and the posterior distributions combined." (Measuring the Velocity Structure)
   - software: eddy
   - parameter: Annulus width 25 mas  
  > "each 25 mas wide (roughly 1/4 of the beam FWHM)" (Measuring the Velocity Structure)
   - fitting: Maximum likelihood with a Gaussian Process on the stacked spectra  
  > "maximised the likelihood when a Gaussian Process was fit to the shifted and stacked data" (Measuring the Velocity Structure)
   - validation: Repeated with v_R fixed to 0, giving no change in v_phi  
  > "we repeat the procedure fixing $v_{R, {\rm proj}} = 0$ and find no change in the inferred $v_{\phi,\, {\rm proj}}$" (Measuring the Velocity Structure)
5. **Measure v_Z from the line centre**: Resample the stacked spectra to 40 m/s and fit a Gaussian, first to the whole spectrum and then to the line core; the line centre is v_LSR plus v_Z,proj  
  > "The measured line center is then considered the sum of the systemic velocity, $v_{\rm LSR}$ and the projected vertical velocity" (Measuring the Velocity Structure)
   - software: eddy
   - parameter: Resampled to 40 m/s, a factor of 16 higher than the original data  
  > "we resample the stacked spectra to ${40}~{\rm m\,s^{-1}}$, a factor of 16 higher than the original data" (Measuring the Velocity Structure)
   - assumption: Deprojection with i = 46.7 deg  
  > "the projected velocity components were corrected for their projection using a disk inclination of $46.7\ensuremath{^\circ}$" (Measuring the Velocity Structure)
   - fitting: _not stated_
   - validation: Differences between the two emission surfaces used for systematics  
  > "We also use the differences between the two methods to estimate the systematic uncertainties on the derived velocities." (Measuring the Velocity Structure)
6. **Subtract background rotation and convert to Mach number**: Fit a 10th-order polynomial to v_phi as a baseline; derive temperature from the peak brightness with the full Planck law and compute the sound speed  
  > "we fit a 10th-order polynomial to $v_{\phi}$" (Measuring the Velocity Structure)
   - assumption: Line is optically thick; brightness temperature traces gas temperature  
  > "we use the brightness temperature of the optically thick line emission as a measure the local gas temperature" (abstract)
   - fitting: _not stated_
   - validation: Polynomial is for presentation only; power laws were tried and rejected  
  > "We stress that this is for presentation purpose only" (Measuring the Velocity Structure)
7. **3D hydrodynamic comparison**: FARGO3D isothermal simulation with three planets for 1.44 Myr  
  > "using publicly available planet-disk interaction code FARGO3D" (Hydrodynamic Simulation Setup)
   - software: FARGO3D
   - parameter: Grid 256x36x635; r = 32.1 to 401.5 au; alpha = 1e-3; Mgas = 0.09 Msun  
  > "We adopt 256 logarithmically-spaced grid cells in the radial direction, 36 uniformly-spaced grid cells in the meridional direction, and 635 uniformly-spaced grid cells in the azimuthal direction." (Hydrodynamic Simulation Setup)
   - fitting: _not stated_
   - validation: Rerun at twice the resolution for 0.432 Myr; the circulation is unchanged  
  > "We confirm that the meridional circulation pattern and its strength are not affected by the change in numerical resolution." (Additional Hydrodynamic Simulations)

## Software

- **bettermoments** : Line-centre maps  
  > "We first make a map of the line centres using `bettermoments`" (Deriving an Emission Surface)
- **eddy** : Emission-surface posteriors and velocity profiles  
  > "using the Python implementation `eddy`(cite: eddy)" (Measuring the Velocity Structure)
- **FARGO3D** : Hydrodynamic simulations  
  > "using publicly available planet-disk interaction code FARGO3D(cite: benitez16)" (Hydrodynamic Simulation Setup)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stellar mass | 2.022 | +/-0.004 | Msun | 2 | $M_{\rm star} = 2.022_{-0.004}^{+0.004}~M_{\rm sun}$ |
| v_LSR | 5.763 | +/-0.001 | km/s | 2 | $v_{\rm LSR} = 5.763_{-0.001}^{+0.001}~{\rm km\,s^{-1}}$ |
| Inclination (fit) | 46.8 | +/-0.1 | deg | 2 | $i = 46.8_{-0.1}^{+0.1}$ |
| Emission surface Z0, phi | Z0 = 265 mas, phi = 1.29 | Z0 +/-3 mas; phi +0.04/-0.03 | mas; dimensionless | 2 | $Z_0 = 265_{-3}^{+3}~{\rm mas}$, $\varphi = 1.29_{-0.03}^{+0.04}$ |
| Statistical uncertainty on v_phi and v_R | ~10 | not stated | m/s | 4 | The resulting statistical uncertainties on $v_{\phi}$ and $v_{R}$ are $\sim$ ${10}~{\rm m\,s^{-1}}$ |
| Gas temperature range | ~90 K inside 30 au to 30 K at 400 au | not stated | K | 6 | finding values spanning between $\approx 90$ K in the inner 30 au and dropping to 30 K at 400 au |
| Outer radial outflow speed | ~30 | not stated | m/s | 4 | the measured $v_{\rm flow} \sim 30~{\rm m\,s^{-1}}$ |

## Qualitative findings

- Three collapsing flow regions coincide with the gaps at 87, 140 and 237 au, and a radial outflow lies beyond ~300 au  
  > "we find three regions of a collapsing flow (Fig. [2](#fig:12COvectors)b)" (abstract)

## Claim tuples

- H: Do gaps in HD 163296 host meridional flows? | E: Measure v_phi, v_R and v_Z from 12CO and compare with a 3D hydro simulation | R: Downward flows with speeds of ~0.1 cs at the gap radii | F: The velocities resemble meridional flows driven by embedded planets, though zonal flows cannot be excluded | **supported**
- H: Is there an outflow in the outer disk? | E: Measure v_R beyond 300 au | R: A persistent radial outflow of ~30 m/s | F: Possibly the base of a disk wind, but it depends on the emission surface | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Viscous spreading is ruled out for the outflow because it would give velocities below 1 m/s  
  > "Viscous spreading of the disk can be ruled out" (abstract)
- How they decided it was enough: _not stated_
- Limitation (authors): v_Z is only relative because v_LSR is uncertain; systematics are 2-3 times the statistical errors  
  > "the inferred $v_{Z}$ radial profiles are therefore only relative values" (Measuring the Velocity Structure)
- Caveat (inferred, ours): Optically thick 12CO and the choice of emission surface drive the v_Z result
- Caveat (inferred, ours): Hydro comparison is qualitative and the simulation overestimates rotational deviations
- Caveat (inferred, ours): Zonal flows are not ruled out

## Reproducibility

- Data public (paper): Raw data in the ALMA archive; images and scripts on the DSHARP website  
  > "We use the publicly available images from the Disk Substructures at High Angular Resolution Program (DSHARP) ALMA large program" (Observations)
- Products in archive: _not stated_
- Code: bettermoments and eddy are on GitHub  
  > "The Python packages used for the analysis of the data are available via their GitHub repositories" (Methods)
- Missing: Exact DSHARP cube file and Delta V for the line-core fit
- Missing: Simulation boundary conditions and planet potential smoothing
- Data volume (inferred): ~ a few GB (DSHARP 12CO image cube)
- Score (inferred): 4/5, Public images and public code with posterior values and settings given; a few details are missing.
- Rediscovery candidate: yes, The data are public, the recipe is largely complete, and the results are numeric.

## Links

- Method: Teague et al. 2018a,b (Velocity-extraction method)
- Method: Pinte et al. 2018a (Non-parametric emission surface)
- Method: Isella et al. 2018 (Data reduction and imaging)
- Companion: Andrews et al. 2018 (DSHARP overview)
- Related: DSHARP

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 47,
  "rate": 0.547
 },
 "evidence_ok": true
}
```
