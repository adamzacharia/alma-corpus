# Kinematic Evidence for an Embedded Protoplanet in a Circumstellar Disk

`2018ApJ...860L..13P` | The Astrophysical Journal Letters 2018 | first author: Pinte, C. | arXiv: 1805.10293 | DOI: 10.3847/2041-8213/aac6dc

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, exoplanets
- Question: Is there a localized deviation from Keplerian velocity in the HD 163296 disc that indicates an embedded protoplanet, and what planet mass and location would explain it?  
  > "We present the detection of a large, localized deviation from Keplerian velocity in the protoplanetary disc surrounding the young star HD 163296." (abstract)
- Target **HD 163296**: coordinates _not stated_; z/distance 101.5 ± 1.2 pc  
  > "HD 163296 is a $\sim$4.4Myr old Herbig Ae star located at a distance of $101.5
\pm 1.2$ pc from the Sun (cite: Gaia-Collaboration2018)." (Introduction); distance from Gaia Collaboration 2018  
  > "HD 163296 is a $\sim$4.4Myr old Herbig Ae star located at a distance of $101.5
\pm 1.2$ pc from the Sun (cite: Gaia-Collaboration2018)." (Introduction)

## Data provenance

- ALMA projects: 2011.0.000010.SV, 2013.1.00601.S, 2011.0.00010.SV
- bands: Band 7 and Band 6  
  > "at Band 7 (2011.0.000010.SV), and on 2015 August 5, 8, and 9 at Band 6 (2013.1.00601.S)" (2 Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 7 beam 0.52'' x 0.38'' PA=82 deg; Band 6 beam 0.28'' x 0.18'' PA=-88 deg  
  > "with a $0.52''
\times 0.38''$ beam at PA=82$^\circ$, and a channel width of 0.11 km s$^{-1}$" (2 Observations and data reduction); "to obtain a synthesized beam of $0.28'' \times
0.18''$ at PA=-88$^\circ$" (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Band 7: 2012 June 9, 11, 22, July 6; Band 6: 2015 August 5, 8, 9  
  > "Observations were performed on 2012 June 9, 11, 22, and July 6 at Band 7" (2 Observations and data reduction)
- pi or archival as stated: Archival ALMA data  
  > "We use archival ALMA data." (2 Observations and data reduction)
- Line: 12CO J=2-1 and 3-2 (not stated)
- Line: 13CO and C18O not stated (not stated)
- Other facility **HST**: Scattered-light disc and gap at ~260-270 au (from literature)  
  > "Observations with the Hubble Space Telescope (HST) revealed a disc in scattered light that extends as far out as 375 au" (Introduction)
- External data: Band 7 channel maps re-used from earlier work  
  > "For the Band 7 data, we re-used the maps produced by (cite: de-Gregorio-Monsalvo2013)" (2 Observations and data reduction) [from (cite: de-Gregorio-Monsalvo2013)]
- External data: Stellar mass 1.9 Msun  
  > "HD 163296 has a mass of $1.9$ M$_{\odot}$ (cite: Flaherty2015)" (Introduction) [from (cite: Flaherty2015)]
- External data: Luminosity 25 Lsun  
  > "a luminosity of $25$ L$_{\odot}$ (cite: Natta2004)" (Introduction) [from (cite: Natta2004)]
- External data: Gas disc parameters for the simulations  
  > "We adopted the gas disc parameters from (cite: de-Gregorio-Monsalvo2013)." (5 Models and discussion) [from (cite: de-Gregorio-Monsalvo2013)]
- Simulation/model as data: Phantom SPH simulations with a 1, 2, 3 or 5 MJup planet at 260 au, post-processed with mcfost into synthetic 12CO J=2-1 channel maps  
  > "We embedded a single planet in the disc orbiting at 260 au with a mass of either 1, 2, 3, or 5 M$_{\rm Jup}$." (5 Models and discussion)

## Processing

### Calibration

- pipeline or manual: CASA scripts provided by ALMA for Band 6  
  > "We used casa scripts provided by ALMA to calibrate the Band 6 data." (2 Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Three rounds of phase self-cal (last at 6 s per integration), then phase and amplitude self-cal; applied to CO lines  
  > "We performed three successive rounds of phase self-calibration, the last with solutions calculated for each individual integration (6s), followed by a phase and amplitude self-calibration." (2 Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = -0.5  
  > "using Briggs weighting with a robust parameter of -0.5" (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Not subtracted  
  > "We did not subtract the continuum emission in order to avoid underestimating the gas temperature" (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Imaging at 0.1 km/s velocity resolution  
  > "Imaging was performed at 0.1 km s$^{-1}$ resolution" (2 Observations and data reduction)
- final beam: 0.28'' x 0.18'' PA=-88 deg (Band 6)  
  > "to obtain a synthesized beam of $0.28'' \times
0.18''$ at PA=-88$^\circ$" (2 Observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- Full data description  
  > "A complete description of the data was presented in (cite: de-Gregorio-Monsalvo2013) and (cite: Isella2016a)." (2 Observations and data reduction) [from (cite: de-Gregorio-Monsalvo2013); (cite: Isella2016a)]
- Method to locate CO emitting layers and velocity kink  
  > "Using the formalism developed in (cite: Pinte2018), we find that the velocity kink is located at a distance of $\approx$ 260 au" (5 Models and discussion) [from (cite: Pinte2018)]
- CO abundance prescription  
  > "We set the CO abundance following the prescription in Appendix B of (cite: Pinte2018)" (5 Models and discussion) [from (cite: Pinte2018)]

### Not stated but needed to reproduce (our reading)

- Spectral windows and line-free channels
- Image size and cell size
- Cleaning threshold, mask and deconvolver
- Number of antennas and baselines/configurations
- Self-calibration solution intervals other than the 6 s one, and reference antenna
- Band 7 map details beyond the beam
- Exact line rest frequencies
- Procedure for comparing synthetic and observed maps (convolution, inclination, PA, systemic velocity)
- Disc inclination and position angle used in mcfost
- Stellar and ring parameters for the temperature model
- Pinte et al. in prep. CO surface and velocity profile

## Analysis recipe

1. **Calibrate and image Band 6 CO data**: ALMA calibration scripts, self-calibration, Briggs imaging at 0.1 km/s without continuum subtraction  
  > "We used casa scripts provided by ALMA to calibrate the Band 6 data." (2 Observations and data reduction)
   - software: CASA
   - parameter: robust = -0.5; August 5 and 8 data only  
  > "we selected only the data from the August 5 and 8 for the analysis" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Locate kink in isovelocity curves**: Inspect channel maps for asymmetry in upper-surface isovelocity curve; derive position with Pinte et al. 2018 formalism  
  > "The emission feature — highlighted by the dotted circle — corresponds to a kink in the upper-surface isovelocity curve northwest of the central object" (3 Results and analysis)
   - parameter: Kink at ~260 au radius, ~70 au above midplane; velocity ~1 km/s from systemic  
  > "the velocity kink is located at a distance of $\approx$ 260 au, and an elevation above the midplane of $\approx$ 70 au" (5 Models and discussion)
   - fitting: _not stated_
   - validation: Same feature seen in 12CO 2-1 and 3-2  
  > "We detect a similar deformation of the isovelocity curves at the same location in both $^{12}$CO $J=2-1$ and $3-2$ transitions" (3 Results and analysis)
3. **Hydrodynamic simulations of embedded planet**: 3D gas-only SPH with phantom, planets of 1, 2, 3, 5 MJup at 260 au, evolved 35 orbits  
  > "We evolved the models for 35 orbits of the planet ($\approx 100,000$ years)" (5 Models and discussion)
   - software: phantom, splash
   - parameter: 1 million SPH particles; central mass 1.9 Msun; disc 50-500 au; gas mass 1e-2 Msun; Sigma critical radius 100 au, p=-1.0, gamma=0.8; H/R 0.08 at 50 au; alpha 1e-3  
  > "We set the gas mass between those radii to $10^{-2}$ M$_\odot$, and use an exponentially tapered power-law surface density profile with a critical radius of 100 au" (5 Models and discussion)
   - assumption: Gas only, dust ignored; vertically isothermal  
  > "We employed gas-only simulations, ignoring the effect of dust" (5 Models and discussion)
   - fitting: _not stated_
   - validation: _not stated_
4. **Synthetic CO channel maps**: mcfost Monte Carlo radiative transfer on Voronoi cells from SPH particles, LTE  
  > "we used the mcfost Monte Carlo radiative transfer code (cite: Pinte06; Pinte09), assuming $T_\mathrm{gas} = T_\mathrm{dust}$" (5 Models and discussion)
   - software: mcfost
   - parameter: Star R=2.1 Rsun, Kurucz 9,250 K; turbulent velocity 50 m/s; grains 0.03-1000 um, a^-3.5; astrosilicate  
  > "The central star was represented by a sphere of radius 2.1 R$_\odot$, radiating isotropically with a Kurucz spectrum at 9,250 K." (5 Models and discussion)
   - assumption: Gas-to-dust ratio 100; CO freeze-out below 20 K  
  > "a gas-to-dust ratio of 100, and computed the dust optical properties using Mie theory" (5 Models and discussion)
   - fitting: No formal fit; visual comparison of predicted and observed channel maps  
  > "A 2 M$_\mathrm{jup}$ planet appears to reproduce a deformation of the $^{12}$CO isovelocity curve that is consistent with the observations." (5 Models and discussion)
   - validation: _not stated_

## Software

- **CASA** : Calibration and imaging of ALMA data  
  > "CASA (cite: McMullin07), phantom (cite: Price2017), splash (cite: Price2007), mcfost (cite: Pinte06; Pinte09)." (Software)
- **phantom** : SPH simulations  
  > "we performed a series of 3D global simulations using the phantom Smoothed Particle Hydrodynamics (SPH) code" (5 Models and discussion)
- **splash** : Visualisation of SPH output (listed in Software)  
  > "CASA (cite: McMullin07), phantom (cite: Price2017), splash (cite: Price2007), mcfost (cite: Pinte06; Pinte09)." (Software)
- **mcfost** : Temperature and synthetic line maps  
  > "To compute the temperature and synthetic line maps, we used the mcfost Monte Carlo radiative transfer code" (5 Models and discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Planet mass | ≈2 | not stated | MJup | 4 | consistent with the dynamical effect of a two-Jupiter-mass planet orbiting at a radius $\approx$ 260 au from the star. |
| Velocity deviation from Keplerian | ≈0.4 (≈15%) | not stated | km/s | 2 | A local deviation of $\approx$ 0.4 km s$^{-1}$ is enough to reproduce the observed spatial shift |
| Projected planet separation | 2.3 | ±0.2 | arcsec | 2 | it would be at a projected distance of 2.3$\pm$0.2" and PA = -3$\pm$5$^\circ$ from the star |
| Planet position angle | -3 | ±5 | deg | 2 | it would be at a projected distance of 2.3$\pm$0.2" and PA = -3$\pm$5$^\circ$ from the star |
| Planet migration in simulation | ≈30 | not stated | au | 3 | the planet migrates by about 30 au during the simulation |

## Qualitative findings

- The deviation is localised in space (~0.5'') and velocity, ruling out axisymmetric ring mechanisms and large-scale structure  
  > "The strongest evidence is that the perturbation to the disc kinematics is highly localised in both space and velocity." (5 Models and discussion)

## Claim tuples

- H: Is there a localized non-Keplerian kink in HD 163296 CO emission? | E: Examined Band 6 and Band 7 12CO channel maps | R: Kink in the isovelocity curve at ~260 au near +1 km/s, seen in both transitions | F: A localized velocity deviation exists | **supported**
- H: Does an embedded planet reproduce the kink, and with what mass? | E: SPH plus radiative transfer models with 1, 2, 3, 5 MJup | R: 2 MJup reproduces it; 1 MJup is too weak; higher masses produce too-strong spirals | F: A ~2 MJup planet at ~260 au is consistent; confirmation needs direct imaging | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Hydrodynamic simulations predict that a planet's impact on the velocity pattern is detectable in high-spectral-resolution ALMA line data  
  > "Hydrodynamic simulations show that the impact on the velocity pattern should be detectable by high spectral resolution ALMA line observations" (Introduction)
- Alternative: Ice lines, self-induced dust traps, instabilities, zonal flows and self-gravity spirals are rejected as causes  
  > "This excludes, for example, ice lines (cite: Zhang2015), self-induced dust traps (cite: Gonzalez2015), instabilities (cite: Takahashi2014; Loren2015) and zonal flows (cite: Flock2015)." (5 Models and discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Confirmation requires direct imaging  
  > "However, confirmation with direct imaging is the only way to be sure." (5 Models and discussion)
- Limitation (authors): Migration rate overestimated by a factor of 2-3 and gap widths and depths are only lower limits  
  > "we overestimate the migration rate by a factor of 2–3 due to the relatively large sink particle radius that we adopted" (Models and discussion)
- Caveat (inferred, ours): Planet mass comes from visual comparison of four simulations with no quantitative fit
- Caveat (inferred, ours): Model is not tuned to HD 163296 in detail
- Caveat (inferred, ours): Other mechanisms are not fully excluded
- Caveat (inferred, ours): Planet position uncertainty relies on half-beam accuracy

## Reproducibility

- Data public (paper): Archival ALMA data  
  > "We use archival ALMA data." (2 Observations and data reduction)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, mask, threshold)
- Missing: mcfost model inclination, PA and systemic velocity
- Missing: Pinte et al. in prep. CO surface
- Missing: Procedure for comparing models and data
- Data volume (inferred): ~100-300 GB (Band 6 and Band 7 raw data)
- Score (inferred): 3/5, Archival data and named codes, but imaging and model-comparison details are missing, and the mass estimate is qualitative.
- Rediscovery candidate: no, Main results rely on visual channel-map comparison with simulations, and imaging details are missing.

## Links

- Method: (cite: Pinte2018) (Method for reconstructing CO emitting layers and velocities)
- Method: (cite: Price2017) (phantom SPH code)
- Companion: (cite: Isella2016a) (Band 6 data description)
- Companion: (cite: de-Gregorio-Monsalvo2013) (Band 7 data description)

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.000010.SV"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 44,
  "rate": 0.564
 },
 "evidence_ok": true
}
```
