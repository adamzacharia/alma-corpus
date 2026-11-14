# Kinematic signatures of a low-mass planet with a moderately inclined orbit in a protoplanetary disk

`2023PASJ...75.1105K` | Publications of the Astronomical Society of Japan 2023 | first author: Kanagawa, Kazuhiro D. | arXiv: 2308.12144 | DOI: 10.1093/pasj/psad059

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: Can a low-mass planet on a moderately inclined orbit produce kinematic (velocity-kink) features in CO channel maps as prominent as a massive coplanar planet, and how do these differ across CO isotopologues?  
  > "We found that a smaller planet, with the inclination being $\sim 10^{\circ}$ – $20^{\circ}$, can produce kinematic features as prominent as those induced by the massive coplanar planet." (abstract)
- Target **HD 163296**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.01055.L
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
- Line: 12CO, 13CO, C18O J=2-1 (not stated)
- Other facility **MAPS (ALMA Large Program)**: HD 163296 12CO, 13CO, C18O channel maps  
  > "for the disks of HD 163296, which is provided by MAPS (cite: MAPS1)." (4.1 Implication to observations)
- External data: Velocity kinks in HD 163296 (outer at 2.2 arcsec in the Δv=1 km/s map; inner at 0.67 arcsec in the Δv=-2.4 km/s map)  
  > "one is seen in the $\Delta v=1$ km/s map at 2.2 arcsec (220 au) (called the outer kink)" (4.1 Implication to observations) [from (cite: Pinte2020)]
- External data: DSHARP dust composition used in the radiative transfer  
  > "We used the same compositions of the dust grains to that adopted in DSHARP (cite: DSHARP_DUST)" (2.3.3 Radiative transfer simulations) [from (cite: DSHARP_DUST)]
- External data: Molecular data from the LAMBDA database  
  > "using molecular data from the LAMBDA database[^4] (cite: Schoier2005; vanderTak2020)." (2.3.3 Radiative transfer simulations) [from (cite: Schoier2005; vanderTak2020)]
- Simulation/model as data: 3D locally isothermal hydrodynamic simulations with Athena++ (Runs 1-11), post-processed with RADMC3D at t=100 orbits  
  > "we used the results of hydrodynamic simulations at $t=100$ orbits, corresponding to $0.1$ Myr when $R_0$=100 au." (2.3.3 Radiative transfer simulations)

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

- Athena++ orbital advection scheme described in a paper in preparation  
  > "with the orbital advection scheme ((cite: Masset2000), see Ono et al. in preparation)" (2.3.1 Hydrodynamic simulations) [from (cite: Masset2000); Ono et al. in preparation]

### Not stated but needed to reproduce (our reading)

- MAPS data product (robust/taper/velocity resolution) used for Figure 13
- Exact velocity channel width and beam for synthetic channel maps
- Full parameter table (Runs 1-11) is not in the text
- Procedure for matching synthetic maps to the observed HD 163296 geometry
- Hydrodynamic code configuration files

## Analysis recipe

1. **Run 3D hydrodynamic simulations of an inclined planet**: Athena++ spherical-grid locally isothermal simulation with alpha=1e-3, planet ramped up over 2π/Ω_K, inclined orbit  
  > "We used Athena++[^1] (cite: Athena++) to solve basic equations" (2.3.1 Hydrodynamic simulations)
   - software: Athena++
   - parameter: H0=0.07 (fiducial) and 0.1; α=1e-3; domain r=0.4-3.0 R0; 192x80x640 cells  
  > "The computational domain runs from $r=0.4R_0$ to $r=3.0R_0$ in $r$-direction" (2.3.1 Hydrodynamic simulations)
   - assumption: Planet torque and migration ignored  
  > "we ignored a torque from the surrounding gas and planetary migration." (2.3.2 Planet)
   - fitting: _not stated_
   - validation: Result unchanged with the second-order van Leer scheme and CFL 0.3  
  > "we confirmed that the result does not change if we chose the second-order van Leer scheme" (2.3.1 Hydrodynamic simulations)
2. **Synthetic CO isotopologue channel maps**: Thermal Monte Carlo for temperature, then LTE line transfer  
  > "First, we calculated the gas temperature by carrying out thermal Monte Carlo simulation by assuming that the gas temperature is equal to the dust temperature." (2.3.3 Radiative transfer simulations)
   - software: RADMC3D, radmc3dPy
   - parameter: distance 140 pc, inclination 45 deg, PA 135 deg, disk mass 0.1 Msun, gas-to-dust 100  
  > "We assumed that the distance from the star was 140 pc and the inclination and position angles were $45^{\circ}$ and $135^{\circ}$, respectively." (2.3.3 Radiative transfer simulations)
   - assumption: 12CO abundance 9.83e-5 relative to H2, 13CO 1.49e-6, C18O 2.26e-7  
  > "The fractional abundance of $^{12}$CO  relative to H$_2$ was set to $9.83\times 10^{-5}$" (2.3.3 Radiative transfer simulations)
   - fitting: _not stated_
   - validation: Vertically isothermal temperature comparison gives similar maps  
  > "except for the magnitude of the intensity, the channel maps is considerably similar to each other." (Appendix: Channel maps in the vertically isothermal disk)
3. **Compare simulated features to HD 163296 MAPS maps**: Visual comparison of 12CO, 13CO, C18O channel maps at the Pinte2020 kink locations  
  > "such a dependence on the isotopologues is consistent with that induced by the inclined planet, rather than the coplanar one." (4.1 Implication to observations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Athena++** : 3D hydrodynamic simulations  
  > "ATHENA++ ((cite: Athena++), https://www.athena-astro.app)" (Software)
- **RADMC3D** 2.0: Thermal Monte Carlo and line radiative transfer  
  > "RADMC3D version 2.0 (cite: Dullemond_Dominik2005) and radmc3dPy python package" (Software)
- **radmc3dPy** : Python interface for RADMC3D  
  > "RADMC3D version 2.0 (cite: Dullemond_Dominik2005) and radmc3dPy python package" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12CO emission layer height z/R0 (H0=0.07) | 0.29 (≃4H0) | not stated | dimensionless | 2 | $z_{\tau=1}/R_0 = 0.29 \simeq 4H_0$ for $^{12}$CO |
| Minimum planet mass to show the anomaly | Mp/M* = 3e-4 (H0=0.07); 5e-4 (H0=0.1); ~0.5 H0^3 | not stated | dimensionless | 2 | the minimum mass may be given by $M_{\rm p}/M_{\ast}\sim 0.5 H_0^3$. |
| v_r perturbation amplitude relative to Keplerian velocity | ~30 % | not stated | % | 1 | its amplitude is approximately 30 % of the Keplerian rotation velocity. |

## Qualitative findings

- Inclined-planet features fade for rarer isotopologues, whereas a coplanar massive planet gives neck and gap structures in 13CO and C18O  
  > "In the case of the inclined planet, the kinematic features is fainter for rarer isotopologues" (Summary)
- Planets in the back layer produce much weaker features, so only about half of such planets are detectable  
  > "only half the planets are detectable" (Summary)

## Claim tuples

- H: A smaller inclined planet can produce kinematic features as clear as a massive coplanar planet | E: 3D hydro plus RADMC3D channel maps for various Mp and i_orb | R: Mp/M*=3e-4 at 10-20 deg gives 12CO features comparable to the coplanar Mp/M*=2e-3 case | F: Inclination can reduce the mass discrepancy between gap and kink estimates | **supported**
- H: Isotopologue dependence distinguishes inclined from coplanar planets | E: Compared 12CO, 13CO, C18O channel maps | R: Rarer isotopologues show weak or no features for the inclined planet, but neck and gap structures for the coplanar planet | F: 13CO and C18O observations can decide the orbital inclination | **supported**
- H: The HD 163296 kinks are due to inclined or coplanar planets | E: Compared MAPS maps with the simulated features | R: Outer kink at 220 au lacks 13CO/C18O features; inner kink at 67 au has neck and gap structures | F: Outer kink is consistent with an inclined planet, inner kink with a coplanar planet | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Temperature in the radiative transfer is inconsistent with the locally isothermal hydrodynamics; the inner boundary may cause artifacts; the tail feature may come from the unresolved circumplanetary disk  
  > "this tail structure can be the artifact caused by the unresolved circumplanetary disk." (3.5 Comparison with the case with the coplanar planet)
- Limitation (authors): Inclination damping is not included  
  > "The orbital inclination is damped due to disk–planet interaction; however, we did not consider this in our paper." (4.2 Possible mechanisms)
- Caveat (inferred, ours): Comparison with HD 163296 is qualitative and visual, with no quantitative fit
- Caveat (inferred, ours): The locally isothermal EOS and fixed CO abundance affect emission-layer heights
- Caveat (inferred, ours): Low vertical resolution; only one snapshot at 100 orbits
- Caveat (inferred, ours): Inclination damping is ignored, so persistence of the inclination is unproven

## Reproducibility

- Data public (paper): MAPS data used for comparison; the ALMA project code is acknowledged  
  > "This paper uses the following ALMA data: ADS/JAO.ALMA#2018.1.01055.L." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Run parameter table
- Missing: Athena++ problem file
- Missing: Exact RADMC3D setup
- Missing: MAPS image processing details
- Data volume (inferred): Small for ALMA (MAPS cubes, tens of GB); the simulations dominate the cost
- Score (inferred): 3/5, Simulation setup is well described and the codes are public, but the ALMA comparison is only qualitative and the parameter table and input files are missing.
- Rediscovery candidate: no, The results are mostly qualitative simulation morphology, and the ALMA part is a visual comparison.

## Links

- Method: (cite: Pinte2020) (Velocity kink detection in DSHARP disks)
- Method: (cite: MAPS1) (Source of the HD 163296 channel maps)
- Related: MAPS
- Related: DSHARP

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
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
  "stated": 24,
  "rate": 0.348
 },
 "evidence_ok": true
}
```
