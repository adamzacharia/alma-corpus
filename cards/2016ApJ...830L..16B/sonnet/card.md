# Misaligned Disks in the Binary Protostar IRS 43

`2016ApJ...830L..16B` | The Astrophysical Journal Letters 2016 | first author: Brinch, Christian | arXiv: 1610.03626 | DOI: 10.3847/2041-8205/830/1/L16

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Are the circumstellar and circumbinary disks of the binary protostar IRS 43 aligned with each other and with the binary orbit, and what are the binary orbital parameters?  
  > "we use our continuum measurements to determine the binary separation, _a_ = 74 _±_ 4 AU, and its inclination, _i_ _<_ 30 _[◦]_ ." (abstract)
- Target **IRS 43 (IRAS 16244-2434; VLA 1 and VLA 2)**: coordinates _not stated_; z/distance d=120 pc  
  > "IRS 43 (IRAS 16244-2434) is a binary protostellar system in the Rho Ophiuchus star forming region (d=120 pc; Knude & Høg 1998)." (1. INTRODUCTION); distance from Knude & Høg 1998  
  > "IRS 43 (IRAS 16244-2434) is a binary protostellar system in the Rho Ophiuchus star forming region (d=120 pc; Knude & Høg 1998)." (1. INTRODUCTION)

## Data provenance

- ALMA projects: 2013.1.00955.S, 2013.1.00233.S
- bands: Band 6 (1.1 mm), tuned to 267 GHz  
  > "We used band 6 in our observations and receivers were tuned to 267 GHz (1.1 mm)." (2. OBSERVATIONS AND DATA REDUCTION)
- frequencies and spectral setup: Continuum at 252 GHz (full 2 GHz); HCO+ 267.6 GHz at 61 kHz resolution; HCN 265.9 GHz at 122 kHz; HC18O+ 255.5 GHz  
  > "HCO + was measured at a spectral resolution of 61 kHz corresponding to 68 ms − 1 while HCN was observed at a slightly lower spectral resolution, 122 kHz corresponding to 138 ms − 1" (2. OBSERVATIONS AND DATA REDUCTION)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 1465 m, 36 antennas  
  > "36 antennas were in use on that night providing baselines from 15 meters to 1465 meters." (2. OBSERVATIONS AND DATA REDUCTION)
- angular resolution: 0.23″ × 0.15″ continuum beam; ~0.2″  
  > "restored with a 0.23 ″ × 0.15 ″ beam" (3.1 Dust)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: approximately 1 hour  
  > "spending approximately 1 hour on the source" (2. OBSERVATIONS AND DATA REDUCTION)
- observing dates: 2015 August 28  
  > "IRS 43 was observed by the Atacama Large Millimeter/submillimeter Array (ALMA) on 2015 August 28" (2. OBSERVATIONS AND DATA REDUCTION)
- pi or archival as stated: _not stated_
- Line: HCO+ J=3-2 (267.6 GHz)
- Line: HCN J=3-2 (265.9 GHz)
- Line: HC18O+ J=3-2 (255.5 GHz)
- Other facility **VLA**: Archival astrometry of the stars over 25 years (projects AC0788, AF0443)  
  > "Two additional datasets on IRS 43 were found in the NRAO VLA archive, project numbers AC0788 and AF0443, taken in 2005 and 2007 respectively." (2. OBSERVATIONS AND DATA REDUCTION)
- External data: VLA astrometric positions and proper-motion study 1990-2002  
  > "we also make use of archival data from the Very Large Array (VLA) as well as data published by Girart et al. (2000) and Curiel et al. (2003)." (2. OBSERVATIONS AND DATA REDUCTION) [from Girart et al. (2000); Curiel et al. (2003)]
- External data: Distance of 120 pc  
  > "(d=120 pc; Knude & Høg 1998)" (1. INTRODUCTION) [from Knude & Høg 1998]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Used ALMA-delivered calibration; recalibration gave no significant improvement  
  > "so we settled on using the original version as provided by ALMA." (2. OBSERVATIONS AND DATA REDUCTION)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Tried, negligible improvement; not applied  
  > "so in the end we decided not to self-calibrate." (2. OBSERVATIONS AND DATA REDUCTION)

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

- Additional ALMA continuum data (0.4″×0.3″) from a larger survey of Class I protostars in Ophiuchus  
  > "2013.1.00955.S, PI: Jes Jørgensen; E. Artur et al., in prep." (2. OBSERVATIONS AND DATA REDUCTION) [from E. Artur et al., in prep.]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, robust, cell, size, deconvolver)
- CASA version used
- Measured source positions and per-epoch values/uncertainties for the astrometry (Fig. 3 only)
- Measurement method for flux and positions (e.g. Gaussian fit)
- Velocity cut and PV-diagram extraction settings and Keplerian fit procedure
- PIKAIA settings (population, generations, parameter bounds)
- Which dataset (2013.1.00233.S vs 2013.1.00955.S) supplies each product

## Analysis recipe

1. **Estimate dust and gas mass from continuum**: Optically thin dust mass from flux, with gas-to-dust 100  
  > "we can estimate the dust mass around the stars using," (3.1 Dust)
   - assumption: Dust temperature 15 K, kappa(1.1 mm)=2.7 cm2 g-1, gas-to-dust 100, d=120 pc  
  > "temperature of 15 K and a dust opacity κ at 1.1 mm of 2.7 cm 2 g − 1" (3.1 Dust)
   - fitting: _not stated_
   - validation: _not stated_
2. **Check Keplerian rotation via PV diagrams**: PV diagrams along disk axes with Gaussian fit to peak position per channel; Keplerian curve fit  
  > "The white markers show the peak position and error bar of a Gaussian fit to the emission in each channel." (Figure 2 caption)
   - assumption: VLA 2 disk position angle adopted along the velocity gradient, assumed to be the CO disk of Herczeg et al. (2011)  
  > "We therefore assume that the velocity gradient seen in HCN across VLA 2 is due to this disk" (3.2 Gas)
   - fitting: Keplerian fit by eye/unspecified  
  > "The full white lines show a Keplerian fit which is discussed in Sect. 4." (Figure 2 caption)
   - validation: Compared with inclination of Brinch & Jørgensen (2013)  
  > "This inclination is consistent with the inclination found by Brinch & Jørgensen (2013)." (4. DISCUSSION AND CONCLUSIONS)
3. **Fit binary orbit from astrometry**: Least-squares fits to positions, separation and PA; genetic algorithm fit of Eq. 2 with 6 free parameters  
  > "The fitting is done by a genetic algorithm PIKAIA (Charbonneau 1995). We ran 20,000 optimization runs with different random number generator seeds" (3.3 Astrometry)
   - software: PIKAIA, CASA
   - assumption: Circular orbit; d=120 pc  
  > "assuming a distance of 120 pc" (Table 1)
   - fitting: Gaussians fitted to the distribution of output parameters from 20,000 runs; mean taken as most probable value  
  > "We then fitted Gaussians to the distributions of output parameter values and taking the mean of these Gaussian fits as the most probable parameter value." (3.3 Astrometry)
   - validation: PIKAIA consistent with least squares; reduced chi2 shown  
  > "The best fit provided by PIKAIA is perfectly consistent with the values found by least square fitting" (3.3 Astrometry)

## Software

- **CASA** : Phase calibration of archival VLA datasets  
  > "These two datasets were phase calibrated using CASA and astrometric positions of the protostellar components measured" (2. OBSERVATIONS AND DATA REDUCTION)
- **PIKAIA** : Genetic-algorithm orbit fit  
  > "The fitting is done by a genetic algorithm PIKAIA (Charbonneau 1995)." (3.3 Astrometry)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| VLA 1 continuum flux | 18.5 | not stated | mJy | 1 | The continuum flux of VLA 1 and VLA 2 is 18.5 mJy and 1.9 mJy respectively |
| VLA 2 continuum flux | 1.9 | not stated | mJy | 1 | The continuum flux of VLA 1 and VLA 2 is 18.5 mJy and 1.9 mJy respectively |
| Binary separation (PIKAIA) | 74 | 4 | AU | 3 | Separation (AU) 72 (1) AU a 74 (4) AU a |
| Stellar mass ratio | 0.500 | 0.018 | dimensionless | 3 | Stellar mass ratio – 0.500 (0.018) |
| Total mass (PIKAIA) | 2.01 | 0.47 | Msun | 3 | Total mass (M ⊙ ) 1.80 (0.42) 2.01 (0.47) |
| Orbital period (PIKAIA) | 444.2 | 33.4 | yr | 3 | Period (Years) 451.2 (46.9) 444.2 (33.4) |
| Circumbinary disk inclination | 70 deg for 1.8 Msun (60 deg for 2.01 Msun) | not stated | deg | 2 | is also very well described by a Keplerian profile using a mass of 1.8 M _⊙_ and an inclination of 70 _[◦]_ . |
| VLA 1 disk inclination | 33 (mass 0.9 Msun) | not stated | deg | 2 | we can fit the PV-diagram of the circumstellar disk around VLA 1 using a mass of 0.9 M _⊙_ and an inclination of 33 _[◦]_ |

## Qualitative findings

- Three Keplerian disks (two circumstellar, one circumbinary) are strongly misaligned with each other and with the binary orbit.  
  > "reveal multiple Keplerian disks which are significantly misaligned ( _>_ 60 _[◦]_ ), both in inclination and position angle and also with respect to the binary orbital plane." (abstract)

## Claim tuples

- H: Disks in IRS 43 are aligned with each other and the orbit | E: ALMA HCN/HCO+ kinematics and VLA/ALMA astrometry | R: Disk inclinations ~70°, ~33° and VLA 2 disk PA offset ~90°; orbit i<30° | F: System is strongly misaligned, suggesting turbulent fragmentation or late misaligned infall | **supported**
- H: Orbit of binary can be constrained from 25 years of astrometry | E: Least-squares and PIKAIA fits | R: a=74±4 AU, total mass 2.01±0.47 Msun, mass ratio 0.5 | F: Orbit near face-on, consistent with circular | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Recalibration and self-calibration were tried but gave no significant improvement  
  > "We did experiment with self-calibration of the continuum, but the improvement in signal–to–noise was negligible" (2. OBSERVATIONS AND DATA REDUCTION)
- How they decided it was enough: _not stated_
- Limitation (authors): Signal too weak to prove the VLA 2 velocity gradient is Keplerian, or to find its inclination  
  > "The signal is not strong enough to prove that the velocity gradient across VLA 2 is Keplerian" (3.2 Gas)
- Caveat (inferred, ours): Kinematic fits appear done by eye with no uncertainties
- Caveat (inferred, ours): Constant vs linear separation cannot be distinguished; circular orbit is assumed
- Caveat (inferred, ours): Only 25 years covers a small fraction of a ~450 yr orbit

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters and CASA version
- Missing: Astrometric position tables
- Missing: PIKAIA configuration
- Missing: Keplerian PV fit procedure
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and a short, clear analysis, but imaging and fitting details are largely missing.
- Rediscovery candidate: no, Imaging and astrometry details are insufficient, and the VLA astrometry tables are not given.

## Links

- Method: Charbonneau 1995 (PIKAIA genetic algorithm)
- Method: Lindberg et al. (2014) (Explains linear low-velocity PV emission)
- Companion: Brinch & Jørgensen (2013) (Earlier radiative transfer modelling of IRS 43 circumbinary gas)
- Companion: E. Artur et al., in prep. (Ophiuchus Class I survey source of 2013.1.00955.S data)
- Related: ALMA survey of Class I protostars in Ophiuchus (2013.1.00955.S)

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 30,
  "rate": 0.469
 },
 "evidence_ok": true
}
```
