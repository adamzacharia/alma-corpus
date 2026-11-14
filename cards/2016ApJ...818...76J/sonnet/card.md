# Modeling Dust Emission of HL Tau Disk Based on Planet-Disk Interactions

`2016ApJ...818...76J` | The Astrophysical Journal 2016 | first author: Jin, Sheng | arXiv: 1601.00358 | DOI: 10.3847/0004-637X/818/1/76

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: Can the ring and gap structures of the HL Tau disk seen by ALMA be produced by planet-disk interactions?  
  > "We address the question whether the observed features of HL Tau by ALMA can be produced by planet-disk interactions." (Introduction)
- Target **HL Tau**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- External data: ALMA HL Tau Band 6 and 7 continuum images, ring/gap identification and spectral index profile  
  > "The simulation results are then coupled with 3D radiative transfer calculations to be compared with the observation of Partnership et al. (2015)." (Summary and Discussion) [from (cite: Partnership2015)]
- External data: Initial disk model parameters (disk mass 0.135 Msun etc.)  
  > "We initialize our hydrodynamic simulation using the results from (cite: Kwon2011)." (2.1 Disk gas+dust+planet model) [from (cite: Kwon2011)]
- Simulation/model as data: LA-COMPASS 2D gas+dust hydrodynamic simulations with three fixed planets, post-processed with RADMC-3D at 1 mm  
  > "The model adopted to analyze HL Tau observations makes use of the LA-COMPASS code (cite: Li2005; Li2009; Fu2014) to calculate the planet-disk interaction" (2 Models)

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

### Inherited from earlier work

- Synthetic observation in the Fourier domain and dust opacity calculation  
  > "we “observe” our models and compare them with the ALMA observations in the Fourier domain, following the procedure described in (cite: Isella2009)." (2.2 Dust model) [from (cite: Isella2009)]

### Not stated but needed to reproduce (our reading)

- ALMA visibility data/images used and how they were obtained (project code, calibration)
- Simulated observation uv coverage, inclination and PA used for the model image
- Distance to HL Tau
- Residual map details and fit quality metric
- LA-COMPASS code availability

## Analysis recipe

1. **Run hydrodynamic gas+dust+planet simulations**: 2D polar grid LA-COMPASS with self-gravity, three fixed planets, 0.15 mm dust in short friction time approximation  
  > "The disk extends from 2.4 AU to 156 AU, and is simulated using a polar grid containing 3072 and 768 cells in the radial and azimuthal direction, respectively." (2.1 Disk gas+dust+planet model)
   - software: LA-COMPASS
   - parameter: alpha = 1e-3; M_disk ~7.35e-2 Msun; M* = 0.55 Msun; planets 0.35, 0.17, 0.26 MJup at 13.1, 33.0, 68.6 AU  
  > "Hence we reduce the disk mass to be $M_{\rm{disk}} \approx 7.35 \times 10^{-2}$ $M_{\odot}$" (2.1 Disk gas+dust+planet model)
   - assumption: Initial dust-to-gas ratio of 1%, no migration  
  > "with an initial dust-to-gas ratio of $1\%$" (2.1 Disk gas+dust+planet model)
   - fitting: _not stated_
   - validation: Planet masses chosen by tens of runs to match gap widths and depths  
  > "we have performed tens of disk+planet hydro simulations in order to determine the likely planet mass values" (2.1 Disk gas+dust+planet model)
2. **Radiative transfer and synthetic image**: RADMC-3D thermal Monte Carlo for dust temperature, then ray tracing at 1 mm and Fourier-domain comparison  
  > "We set up a thermal Monte Carlo run to calculate the dust temperature using the radiative transfer code *RADMC-3D*." (2.2 Dust model)
   - software: RADMC-3D
   - parameter: opacity 4.6 cm2/g at 1 mm; MRN n(a)∝a^-3.5, 5e-4 to 10 mm; f_sett = 0.1  
  > "The resulting dust opacity at the wavelength of 1 mm is 4.6 cm$^2$ g$^{-1}$" (2.2 Dust model)
   - assumption: Silicates, organic carbonates and water ice grains  
  > "assuming that dust grains are compact spheres made of astronomical silicates (cite: wd01)," (2.2 Dust model)
   - fitting: _not stated_
   - validation: Compared with ALMA Band 7 image, major-axis profile, and spectral index  
  > "Overall, our model reproduces the observations quite well." (3.1 The nominal model)

## Software

- **LA-COMPASS** : Hydrodynamic planet-disk simulations  
  > "makes use of the LA-COMPASS code (cite: Li2005; Li2009; Fu2014) to calculate the planet-disk interaction" (2 Models)
- **RADMC-3D** : Dust temperature and 1 mm emission  
  > "radiative transfer code *RADMC-3D*[^1] to calculate the disk temperature and emission at 1 mm" (2 Models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Planet masses (nominal model) | 0.35, 0.17, 0.26 | not stated | MJup | 1 | three planets with masses 0.35, 0.17, and 0.26 $M_{Jup}$ at 13.1, 33.0, and 68.6 AU, respectively |
| Eccentricities of gaps | 0.246, 0.274, 0.277 | not stated | dimensionless | 2 | We obtain the eccentricities of gaps as 0.246, 0.274 and 0.277, respectively |
| Eccentricities of rings | 0.191, 0.079, 0.157 | not stated | dimensionless | 2 | whereas the eccentricities of rings as 0.191, 0.079 and 0.157, respectively |

## Qualitative findings

- Disk self-gravity is essential to produce the third gap; halving planet masses fails to produce the second gap; lower viscosity makes gaps too deep  
  > "Run2, where the disk self-gravity is turned off, fails to produce the third gap." (3.2 Influence of parameters)

## Claim tuples

- H: Planet-disk interactions can produce the HL Tau rings and gaps | E: 2D gas+dust hydro with three planets plus RADMC-3D synthetic observation compared with ALMA | R: Model matches major-axis intensity profile, spectral index and gap eccentricity trend at three main gaps | F: Observed features can be mostly reproduced by three planets | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Planets fixed in radius would migrate; outer rings not reproduced with a single outer planet; disk barely stable  
  > "the three planets in our model are assumed to stay on fixed radii. When allowed to migrate, they eventually move out of the current locations." (Summary and Discussion)
- Caveat (inferred, ours): No formal goodness-of-fit or parameter uncertainties; planet masses hand-tuned and degenerate with viscosity, disk mass
- Caveat (inferred, ours): Reduced disk mass versus literature
- Caveat (inferred, ours): Single dust size and 2D simulations

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: LA-COMPASS code and setup files
- Missing: ALMA data details
- Missing: Synthetic observation parameters
- Data volume (inferred): small if only the published images are used
- Score (inferred): 3/5, Simulation parameters are largely given, but code, ALMA data details and fit metrics are missing.
- Rediscovery candidate: no, Main result is simulation-based with hand-tuned fit and unreleased code; ALMA data not specified.

## Links

- Method: (cite: Isella2009) (Opacity calculation and Fourier-domain comparison procedure)
- Companion: (cite: Partnership2015) (Source ALMA HL Tau observations)
- Related: ALMA HL Tau Long Baseline Campaign

## Checks

```json
{
 "quotes": 22,
 "quotes_ok": 22,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00015.SV"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 17,
  "rate": 0.279
 },
 "evidence_ok": true
}
```
