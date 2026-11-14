# Direct mapping of the temperature and velocity gradients in discs. Imaging the vertical CO snow line around IM Lupi

`2018A&A...609A..47P` | Astronomy and Astrophysics 2018 | first author: Pinte, C. | arXiv: 1710.06450 | DOI: 10.1051/0004-6361/201731377

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Can the altitude, velocity and temperature of the CO emitting layers of the IM Lupi disc be measured directly from ALMA channel maps, locating the vertical CO snow line?  
  > "We present here a framework to directly measure the altitude, velocity, and temperature of the CO layers" (Introduction)
- Target **IM Lupi**: coordinates _not stated_; z/distance 161±10 pc  
  > "IM Lupi is a M0V T Tauri star (distance of $161\pm10$ pc, (cite: Gaia16)) surrounded by a large and massive disc with an inclination of $48^\circ\pm3^\circ$" (Introduction); distance from Gaia (Gaia16)  
  > "IM Lupi is a M0V T Tauri star (distance of $161\pm10$ pc, (cite: Gaia16)) surrounded by a large and massive disc with an inclination of $48^\circ\pm3^\circ$" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00798.S
- bands: Band 6  
  > "IM Lupi was observed with ALMA in band 6 on the night from 9 to 10 June 2015" (2 Observations and data reduction)
- frequencies and spectral setup: two TDM windows at 218.9 and 231.7 GHz (1.875 GHz each); two FDM windows for 12CO, 13CO, C18O J=2-1, channel spacing 30.5 kHz, averaging 2, resolution 35 kHz (45-48 m/s)  
  > "The other two spectral windows were configured in Frequency Division Mode (FDM) to target the $^{12}$CO J=2-1, $^{13}$CO J=2-1, and C$^{18}$O J=2-1 transitions, with a channel spacing of 30.5 kHz and a channel averaging of 2." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 21.4 to 784 m, 37 antennas  
  > "The array was configured with 37 antennas and baselines ranging from 21.4 to 784 m." (2 Observations and data reduction)
- angular resolution: about 0.36" x 0.55" (continuum)  
  > "0.36” $\times$ 0.55” at -80$^\circ$" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 37.4 min  
  > "with a total on-source time of 37.4 min" (2 Observations and data reduction)
- observing dates: 9-10 June 2015  
  > "on the night from 9 to 10 June 2015" (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- External data: Distance 161±10 pc  
  > "distance of $161\pm10$ pc, (cite: Gaia16)" (Introduction) [from (cite: Gaia16)]
- External data: Disc inclination 48±3 deg  
  > "inclination of $48^\circ\pm3^\circ$ (cite: Pinte08; Cleeves16)" (Introduction) [from (cite: Pinte08; Cleeves16)]
- Simulation/model as data: MCFOST illustrative disc model with CO chemistry (photodissociation, freeze-out below 21 K, photodesorption), fitted with a genetic algorithm to Band 6 CO data  
  > "we only adjusted the Band 6 CO data in the image place via a genetic algorithm (each generation was composed of 100 models and the genetic algorithm was run for 50 generations)" (Model description and parameters)

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "The data sets were calibrated using the Common Astronomy Software Applications pipeline" (2 Observations and data reduction)
- casa version: 4.6.0  
  > "version 4.6.0" (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "Titan was used as a flux calibrator" (2 Observations and data reduction)
- flux scale uncertainty: 10%  
  > "We estimate the flux calibration uncertainty to 10 %." (2 Observations and data reduction)
- self calibration: three rounds of phase self-cal (last per 6 s integration), then phase and amplitude self-cal; continuum solutions applied to CO lines  
  > "We performed three successive rounds of phase self-calibration, the last with solutions calculated for each individual integration (6s), followed by a phase and amplitude self-calibration." (2 Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: manually defined CLEAN mask for continuum and each channel  
  > "A CLEAN mask was manually defined for the continuum image and each channel map." (2 Observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: maps made with and without uvcontsub; no significant difference  
  > "Channel maps were produced both with and without continuum subtraction (using the CASA task *uvcontsub*)." (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 13CO and C18O binned to 80 and 320 m/s channels; 12CO at native width  
  > "for $^{13}$CO and C$^{18}$O we needed to bin the data to channel widths of 80 and 320 m/s, respectively" (3.5 Caveats)
- final beam: 12CO 0.36"x0.56"; 13CO 0.38"x0.58"; C18O 0.38"x0.58"  
  > "0.38” $\times$ 0.58” at -79$^\circ$" (Table 1)
- final rms: continuum 0.05 mJy/beam; moment 0 RMS 3.5, 4.2, 3.9 mJy km/s  
  > "0.05 mJy/beam" (Table 1)

### Inherited from earlier work

- Continuum optical depth via iterative MCFOST modelling procedure  
  > "We use the same iterative procedure as in (cite: Pinte16) for HL Tau." (Continuum optical depth) [from (cite: Pinte16)]
- Disc model extends earlier IM Lupi model with tapered surface density  
  > "Our model is an extension of the model presented in (cite: Pinte08), where the radial power-law surface density was replaced by a tapered-edge structure, following (cite: Panic09)." (Model description and parameters) [from (cite: Pinte08); (cite: Panic09)]
- External radiation field prescription  
  > "We follow the same prescription as (cite: Woitke16)." (Model description and parameters) [from (cite: Woitke16)]

### Not stated but needed to reproduce (our reading)

- CLEAN robust/weighting, cell size, image size, deconvolver and thresholds
- Line-free channels for continuum subtraction
- Rest frequencies and LSR velocity reference
- Systemic velocity value
- Peak-finding algorithm details and uncertainty estimation for h, v, T
- Self-calibration solution intervals and reference antenna
- Stellar position (continuum peak) coordinates
- Genetic algorithm fitness function and parameter bounds
- Whether pipeline or manual calibration scripts were used

## Analysis recipe

1. **Calibrate and image**: CASA calibration, self-calibration on continuum applied to lines, CLEAN with manual masks, with and without uvcontsub  
  > "The continuum self-calibration solutions were applied to the CO lines." (2 Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: consistent with Cleeves16  
  > "Our data and results are consistent with those of (cite: Cleeves16)." (2 Observations and data reduction)
2. **Locate emission maxima along isovelocity curves and derive r, h**: In each channel map, for x sampled every 0.08", find near/far-side maxima y_n,y_f; y_c=(y_f+y_n)/2; r from ellipse geometry; h=(y_c-y_star)/sin i  
  > "The altitude $h$ of the orbit is derived by noting that the offset between the centre of the ellipse and the star is simply $h \sin i$" (3.1 Altitude)
   - parameter: x sampled every 0.08" (~1/4 beam); star at continuum peak  
  > "where we sampled $x$ every 0.08”, i.e. $\approx$ 1/4 of the beam" (3.4 Reconstructing the full spatial, kinematic, and thermal structure of the CO layers)
   - assumption: Circular Keplerian orbits parallel to midplane; inclination 48 deg; no radial or vertical flows  
  > "we assume that, at any point in the disc, the gas is rotating on a circular orbit parallel to the disc midplane" (3.1 Altitude)
   - fitting: Linear regression for power-law altitude exponents  
  > "A linear regression analysis indicates a power-law exponent of 1.8$\pm$0.2 and 2.1$\pm$0.4" (4.1 CO layers)
   - validation: Results compared with continuum-subtracted and non-subtracted maps  
  > "we performed our analysis on both the continuum-subtracted and non-subtracted maps and did not find any significant difference" (3.5 Caveats)
3. **Derive gas velocity**: v=(v_obs-v_syst) r/((x-x_star) sin i); compare with altitude-dependent Keplerian and pressure-gradient terms  
  > "we obtain the actual gas velocity at each point" (3.2 Gas velocity)
   - assumption: Central mass 1 Msun (PV fit), distance 161 pc  
  > "central mass of $1\pm0.1$ M$_\odot$, assuming a distance of 161 pc" (C18O observational results)
   - fitting: _not stated_
   - validation: Compared with MCFOST model pressure-gradient correction  
  > "consistent with the expected pressure gradient as derived from the temperature and density structure of our MCFOST model" (4.3 Vertical velocity gradient and sub-Keplerian rotation)
4. **Gas temperature from brightness temperature**: Peak brightness temperature of optically thick 12CO and 13CO taken as kinetic temperature (LTE); central 12CO channels within ±0.7 km/s excluded  
  > "For optically thick lines, the peak intensity then provides an accurate estimate of the gas temperature." (3.3 Gas kinetic temperature)
   - assumption: T_ex = T_kin (LTE)  
  > "Low J CO lines are close to local thermodynamic equilibrium" (3.3 Gas kinetic temperature)
   - fitting: _not stated_
   - validation: C18O Tb ~8 K implies 13CO tau ~4, consistent with optically thick assumption  
  > "the corresponding $^{13}$CO optical depth is $\approx
4$, confirming our assumption of $T_\mathrm{ex} = T_\mathrm{kin}$" (4.4 Two-dimensional temperature structure and vertical CO snow line)
5. **Illustrative MCFOST model of CO depletion**: MCFOST radiative transfer with simple CO chemistry, parameters fitted by genetic algorithm on Band 6 channel maps; test depletion scenarios  
  > "This model is only meant to provide a qualitative description of the ALMA band 6 data." (Model description and parameters)
   - software: MCFOST
   - parameter: Freezeout at T<21 K with factor epsilon=8e-5  
  > "$\epsilon$                           |   8$\times 10^{-5}$" (Table 1)
   - assumption: Gas temperature equals dust temperature; CO in LTE  
  > "We then assume that the gas temperature is equal to the dust temperature and that the CO emission is at local thermodynamic equilibrium" (Model description and parameters)
   - fitting: Genetic algorithm, 100 models per generation, 50 generations  
  > "each generation was composed of 100 models and the genetic algorithm was run for 50 generations" (Model description and parameters)
   - validation: Qualitative; admitted non-unique  
  > "our model may not be a unique solution" (Model description and parameters)
6. **Continuum optical depth**: Deconvolve major-axis profile, convert to surface density, iterate MCFOST until profile changes <1%  
  > "iteratively correct the surface density until the synthetic brightness profile does not change by more than 1% at any radius" (Continuum optical depth)
   - software: MCFOST
   - assumption: Initial temperature power-law exponent -0.5  
  > "assuming an initial power-law radial temperature profile (exponent = -0.5)" (Continuum optical depth)
   - fitting: _not stated_
   - validation: Convergence after about ten iterations  
  > "We reach convergence after about ten iterations." (Continuum optical depth)

## Software

- **CASA** 4.6.0: calibration, self-calibration, imaging, uvcontsub  
  > "(CASA, (cite: McMullin07), version 4.6.0)" (2 Observations and data reduction)
- **MCFOST** : Monte Carlo radiative transfer disc models and continuum optical depth  
  > "using the radiative transfer code MCFOST (cite: Pinte06; Pinte09)" (4.2 CO depleted midplane)
- **ProDiMo** : calibration of simple CO chemistry prescription (models from Woitke16)  
  > "which was calibrated from ProDiMo models (cite: Woitke16)" (Model description and parameters)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12CO altitude at 200 au | ~65 | not stated | au | 2 | At a distance of 200 au, the $^{12}$CO emission originates from an altitude of $\approx$65 au, while the $^{13}$CO originates from $\approx$25 au. |
| 13CO altitude at 200 au | ~25 | not stated | au | 2 | the $^{13}$CO originates from $\approx$25 au |
| Power-law exponent of 12CO layer altitude (r<300 au) | 1.8 | 0.2 | dimensionless | 2 | power-law exponent of 1.8$\pm$0.2 and 2.1$\pm$0.4 for the altitude of $^{12}$CO and $^{13}$CO |
| Power-law exponent of 13CO layer altitude (r<300 au) | 2.1 | 0.4 | dimensionless | 2 | power-law exponent of 1.8$\pm$0.2 and 2.1$\pm$0.4 |
| 12CO lower-surface temperature (130-300 au) | ~21 | not stated | K | 4 | the $^{12}$CO temperature is virtually constant at $\approx$ 21 K, between 130 and 300 au |
| Temperature at 400 au above snow line | ~15 | not stated | K | 4 | down to $\approx$15 K at 400 au |
| Deviation from altitude-dependent Keplerian at 400 au | ~0.15 | not stated | km/s | 3 | the measured deviations from the altitude dependent Keplerian rotation are of the order of $0.15$ km/s |
| Central stellar mass | 1 | 0.1 | Msun | 3 | central mass of $1\pm0.1$ M$_\odot$ |
| 1.3 mm continuum flux | 225 | 23 | mJy | 1 | 225 $\pm$ 23 mJy |
| 12CO (2-1) integrated flux | 24.1 | 2.4 | Jy km/s | 1 | 24.1 $\pm$ 2.4 Jy.km/s |
| Maximum continuum optical depth outside 100 au | ~0.03 | not stated | dimensionless | 6 | the maximum optical depth is $\approx 0.03$ |

## Qualitative findings

- 12CO layer lies above 13CO; 13CO and C18O co-spatial, marking the vertical CO freeze-out layer  
  > "The fact that we do not see any significant difference in altitude between $^{13}$CO and C$^{18}$O suggests that we are actually probing a physical layer in the disc" (4.1 CO layers)
- Gas becomes sub-Keplerian beyond ~300-350 au, possibly from pressure gradient or photo-evaporative wind  
  > "At larger radii, the gas becomes clearly sub-Keplerian." (4.3 Vertical velocity gradient and sub-Keplerian rotation)

## Claim tuples

- H: CO layer altitude can be measured model-independently from channel maps | E: Locate emission maxima on isovelocity curves for 12CO, 13CO, C18O | R: 12CO at ~65 au vs 13CO ~25 au at 200 au; exponents 1.8 and 2.1 | F: First direct model-independent measurement of CO layer altitudes | **supported**
- H: CO is depleted in the midplane | E: Compare lower-surface morphology with MCFOST models | R: Partial depletion of ~1e-4 where T<20 K reproduces the shifted lower surface | F: CO needs to be physically depleted in the midplane | **supported**
- H: The vertical CO snow line temperature can be measured directly | E: Brightness temperature of 12CO lower surface and 13CO upper surface | R: Plateau at ~21 K between 130 and 300 au | F: CO condensation temperature ~21 K | **supported**
- H: Velocity field shows vertical gradient and sub-Keplerian rotation | E: Compare measured velocities with altitude-dependent Keplerian | R: Agreement within 300 au; ~0.15 km/s deviation at 400 au | F: Pressure gradient may explain it, wind possible | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Intermediate-inclination discs have Keplerian velocities that spatially separate emitting regions  
  > "Discs at intermediate inclinations are also ideal targets as the Keplerian velocities spatially separate the emitting regions" (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Method only valid to ~450 au and where emission is a thin layer; accuracy limited by ~0.4" resolution  
  > "These conditions are met for the CO layers of IM Lupi up to a radius 450 au" (3.5 Caveats)
- Limitation (authors): Illustrative model not unique, not optimized  
  > "is not in any sense optimized and should only be considered for general guidance" (4.2 CO depleted midplane)
- Caveat (inferred, ours): No uncertainties for individual h, v, T points; peak-finding errors not propagated
- Caveat (inferred, ours): Beam smearing and finite resolution may bias altitude and temperature near the star
- Caveat (inferred, ours): Model dependence of lower-surface interpretation and 21 K vs. depletion degeneracy
- Caveat (inferred, ours): Single object

## Reproducibility

- Data public (paper): ALMA program 2013.1.00798.S cited in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00798.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters (robust, cell, image size)
- Missing: Peak-finding code and procedure
- Missing: Systemic velocity and stellar position values
- Missing: Genetic algorithm details
- Data volume (inferred): ~10-30 GB
- Score (inferred): 5/5, Public data and clear geometric method, but imaging parameters, code and uncertainty estimation are not given.
- Rediscovery candidate: yes, Public archival data, geometric method fully described by equations, numeric results (21 K plateau, altitudes, exponents).

## Links

- Method: (cite: Pinte16) (iterative continuum optical depth procedure)
- Method: (cite: Boehler17) (continuum subtraction effects on optically thick lines)
- Companion: (cite: Cleeves16) (previous IM Lupi ALMA observations and global model)
- Companion: (cite: Dutrey17) (related method for edge-on discs)

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 55,
  "rate": 0.679
 },
 "evidence_ok": true
}
```
