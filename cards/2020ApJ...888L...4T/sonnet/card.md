# Long-lived Dust Rings around HD 169142

`2020ApJ...888L...4T` | The Astrophysical Journal Letters 2020 | first author: Toci, Claudia | arXiv: 1911.08580 | DOI: 10.3847/2041-8213/ab5c87

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: Can two giant planets in resonant locking explain the long-lived inner dust rings and gas cavity of HD 169142?  
  > "we model the two prominent dust rings and the cavity of HD 169142 including in the system two giant planets, in order to check whether this substructure is a transient or is actually a long lived feature" (Introduction)
- Target **HD 169142**: coordinates _not stated_; z/distance 117 ± 4 pc  
  > "Its distance is 117 $\pm$ 4 pc (cite: Gaia2016)." (Introduction); distance from Gaia Collaboration 2016  
  > "Its distance is 117 $\pm$ 4 pc (cite: Gaia2016)." (Introduction)

## Data provenance

- ALMA projects: 2013.1.00592.S
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
- External data: 1.3 mm continuum and CO isotopologue observations and DALI thermochemical model (reference profile)  
  > "Our reference profile for the gas and dust distributions is the DALI thermochemical model from FD17" (Results) [from Fedele et al. 2017 (cite: Fedele2017)]
- External data: High-resolution 1.3 mm continuum images with triple outer ring  
  > "recently resolved as a system of three thin rings by observations of PS19" (Introduction) [from Pérez et al. 2019 (cite: Perez2019)]
- External data: 3.1 mm and 0.890 mm ALMA observations used for comparison  
  > "in good agreement with ME18 observations (c.2 and d.2 respectively)" (Results) [from Macias et al. 2018 (cite: Macias2018)]
- External data: 13CO J=3-2 ALMA archive data used to update the gas cavity location to ~20-56 au  
  > "Based on the $^{13}$CO J=3-2 ALMA archive data from (cite: Honda2012), the gas cavity appears to be located at $\sim 20-56$ au." (Results) [from (cite: Honda2012)]
- Simulation/model as data: PHANTOM SPH simulation with two migrating, accreting planets, post-processed with MCFOST  
  > "We perform 3D global simulations of dust and gas disc with two embedded giant protoplanets using the smoothed particle hydrodynamics (SPH) code PHANTOM" (Hydrodynamical simulation)

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

- Aspect ratio H/R=0.07 and p=q=0.5 adopted  
  > "We also assumed an aspect ratio value of $\rm{H/R}=0.07$ at $\rm{R=R}_{\rm{ref}}$ and $p=q=0.5$ as found in FD17." (Hydrodynamical simulation) [from FD17 (cite: Fedele2017)]
- Gas-to-dust ratio of 80  
  > "assuming a gas-to-dust ratio of 80 as inferred from FD17 CO isotopologous measurements" (Hydrodynamical simulation) [from FD17 (cite: Fedele2017)]
- Disc setup in PHANTOM  
  > "We set up the discs in PHANTOM using the setup from (cite: Lodato2010)." (Hydrodynamical simulation) [from (cite: Lodato2010)]

### Not stated but needed to reproduce (our reading)

- Exact reference radius R_ref
- Synthetic imaging and beam convolution details
- How ALMA data from 2013.1.00592.S were processed, if used
- Simulation snapshot and output files
- MCFOST photon numbers and inclination handling details

## Analysis recipe

1. **Run SPH simulation**: 3D PHANTOM single-fluid dust-gas simulation with two migrating, accreting sink-particle planets  
  > "We consider a star with mass 1.65 M$_\odot$ and two planets allowed to migrate and accrete mass." (Hydrodynamical simulation)
   - software: PHANTOM
   - parameter: 10^6 SPH particles, R_in=5 to R_out=150 au, alpha_SS=0.005, 1 mm grains  
  > "a disc of $10^6$ SPH particles, extending from $\rm{R}_{\rm{in}} = 5$ to $\rm{R}_{\rm{out}} = 150$ au." (Hydrodynamical simulation)
   - assumption: Locally isothermal; initial gas mass ~1e-2 Msun; dust mass 1.2e-4 Msun  
  > "The initial dust mass is $1.2 \times 10^{-4} \rm{M}_\odot$" (Hydrodynamical simulation)
   - fitting: _not stated_
   - validation: Tested stellar accretion radius of 1 au, no significant differences  
  > "We also tested our results for an accretion radius of 1 au, finding no significant differences." (Hydrodynamical simulation)
2. **Radiative transfer and synthetic observations**: Post-process with MCFOST and compare with ALMA observations  
  > "we post-process our simulation using the Monte Carlo radiative transfer code MCFOST" (Radiative transfer model)
   - software: MCFOST
   - parameter: Grain size slope -3.5, 0.03 um to 3 mm; Teff~8000 K; R~2.2 Rsun; 117 pc; inclination 13 deg; PA 5 deg  
  > "The grain size distribution has a slope of $-3.5$ and goes from 0.03 $\mu$m to 3 mm." (Radiative transfer model)
   - assumption: 70% silicates, 30% carbonaceous, 10% porosity  
  > "supposing a chemical composition for the dust grains of 70$\%$ silicates and 30$\%$ carbonaceus material, with a porosity level of 10$\%$" (Results)
   - fitting: _not stated_
   - validation: Visual comparison with observed 1.3 mm, 3.1 mm and 0.89 mm images and radial profiles  
  > "The ring profile is well reproduced and the value of the flux is consistent with the observation." (Results)

## Software

- **PHANTOM** : SPH hydrodynamical simulation  
  > "using the smoothed particle hydrodynamics (SPH) code PHANTOM" (Hydrodynamical simulation)
- **MCFOST** : Monte Carlo radiative transfer post-processing  
  > "Monte Carlo radiative transfer code MCFOST" (Radiative transfer model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Best-agreement time | 160 T_orb = 5e4 yr | not stated | yr | 1 | obtained after $160~\rm{T}_{orb} = 5 \times 10^{4}$ yr |
| Planet masses at best match | ~2.4 | not stated | M_J | 1 | with almost equal masses, $\sim 2.4$ M$_J$ |
| Planet locations | 17.4 and 50 | not stated | au | 1 | The inner planet is located at $\sim 17.4$ au and the outer at $\sim50$ au |
| Dust ring lifetime | >= 2e5 | not stated | yr | 1 | preserved for at least $\sim$ 500 orbits, i.e for over $\sim 2\times 10^5$ yr |
| Disc total mass and dust mass | ~6e-3 and ~0.9e-4 | not stated | M_sun | 1 | The total mass of the disc is $\sim 6\times 10^{-3}$ M$_\odot$ and the dust mass is $\sim 0.9\times 10^{-4} ~\rm{M}_\odot$. |

## Qualitative findings

- The inner planet sits at the inner edge of the dust ring and accretes dust, producing a feature that could be observed with ALMA and might rotate ~5 deg per year  
  > "as the planet is expected to rotate by a 5 degree angle in one year" (Results)

## Claim tuples

- H: Two resonant giant planets produce long-lived dust rings and a gas cavity | E: PHANTOM simulation plus MCFOST synthetic images compared with ALMA | R: Dust ring persists >2e5 yr; planets ~2.4 MJ at 17.4 and 50 au in 5:1 resonance | F: The configuration reproduces the inner rings and cavity | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: A third planet for the outer ring splitting was not included, as outside the paper's purpose  
  > "We choose not to include a third body (as predicted by PS19), used to model also the outer ring splitting." (Hydrodynamical simulation)
- How they decided it was enough: _not stated_
- Limitation (authors): Instant accretion at the sink radius may overestimate planet accretion  
  > "This may over-estimate the accretion onto the planet" (Hydrodynamical simulation)
- Caveat (inferred, ours): Single simulation with one set of initial conditions; no parameter exploration
- Caveat (inferred, ours): Agreement with observations is qualitative, with no quantitative fit
- Caveat (inferred, ours): Parameter degeneracies (planet masses, alpha) are not explored

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Simulation input files
- Missing: Image-comparison procedures
- Missing: Processed ALMA data
- Data volume (inferred): Small; mainly simulation compute, with a few GB if archival ALMA data are used
- Score (inferred): 3/5, The simulation setup is mostly described but there is no code or inputs, and the ALMA comparison is qualitative.
- Rediscovery candidate: no, The paper is a simulation study whose ALMA comparison is qualitative and whose results are not tied to reduced ALMA data.

## Links

- Method: Price et al. 2018 (cite: Price2017) (PHANTOM code)
- Method: Pinte et al. 2009 (cite: Pinte2009) (MCFOST code)
- Companion: Fedele et al. 2017 (cite: Fedele2017) (Reference disc model)
- Companion: Pérez et al. 2019 (cite: Perez2019) (High-resolution ALMA continuum)

## Checks

```json
{
 "quotes": 32,
 "quotes_ok": 32,
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
  "stated": 24,
  "rate": 0.364
 },
 "evidence_ok": true
}
```
