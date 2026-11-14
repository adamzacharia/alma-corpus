# Kinematic detection of a planet carving a gap in a protoplanetary disk

`2019NatAs...3.1109P` | Nature Astronomy 2019 | first author: Pinte, C. | arXiv: 1907.02538 | DOI: 10.1038/s41550-019-0852-6

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, exoplanets
- Question: Is a localised deviation from Keplerian flow in 13CO emission of HD 97048 spatially coincident with a dust gap, indicating an embedded planet, and what is its mass?  
  > "An embedded planet can explain both the disturbed Keplerian flow of the gas, detected in CO lines, and the gap detected in the dust disc at the same radius." (abstract)
- Target **HD 97048**: coordinates _not stated_; z/distance 185 pc  
  > "HD 97048 is located in the Chameleon I cloud, at a distance of 185 pc (cite: Gaia-Collaboration2018)." (HD 97048.); distance from Gaia DR2 (Gaia Collaboration 2018)  
  > "HD 97048 is located in the Chameleon I cloud, at a distance of 185 pc (cite: Gaia-Collaboration2018)." (HD 97048.)

## Data provenance

- ALMA projects: 2016.1.00826.S
- bands: Band 7 (885 um continuum)  
  > "We observed HD 97048 with ALMA in band 7 in the C40-4 (1 execution) and C40-7 (2 executions) configurations" (Observations and data reduction.)
- frequencies and spectral setup: One spw centred on 13CO J=3-2, 122 kHz channels, 244 kHz (220 m/s) after Hanning smoothing; three continuum spws of 1.875 GHz  
  > "with an individual channel width of 122 kHz, resulting in a 244 kHz spectral resolution (220 m s$^{-1}$) after Hanning smoothing." (Observations and data reduction.)
- continuum bandwidth: 1.875 GHz per spw, three spws  
  > "The three other spectral windows were used for continuum with a bandwidth of 1.875 GHz each." (Observations and data reduction.)
- arrays: _not stated_
- configurations: C40-4 (1 execution), C40-7 (2 executions)  
  > "in the C40-4 (1 execution) and C40-7 (2 executions) configurations" (Observations and data reduction.)
- baselines: 15 to ~8,500 m  
  > "2017 Nov 24 | 42.7 | 49 | 92 to 8548" (Table 1)
- angular resolution: 0.07"x0.11" (13x20 au)  
  > "resulting in final images with a spatial resolution of 0.07”$\times$0.11” (13$\times$20 au)." (Introduction)
- max recoverable scale: _not stated_
- sensitivity: 3.6 mJy/beam per channel (combined)  
  > "Typical RMS values obtained are 3.6 mJy/beam per channel for the combined data." (Observations and data reduction.)
- time on source: 112 minutes total  
  > "reaching a total time on source of 112 minutes" (Observations and data reduction.)
- observing dates: 2016 Nov 18, 2017 Nov 24, 2017 Nov 30  
  > "2016 Nov 18 | 26.3 | 45 | 15 to 919" (Table 1)
- pi or archival as stated: PI G. van der Plas; proposal written by a co-author  
  > "(ALMA program #2016.1.00826.S, PI: G. van der Plas)" (Observations and data reduction.)
- Line: 13CO J=3-2 (not stated)
- Other facility **VLT/SPHERE**: Scattered light images and point-source detection limit (~2 MJup) from earlier work  
  > "HD 97048 was observed with SPHERE on the VLT, resulting in a point source detection limit of $\approx$2 M$_\mathrm{Jup}$ (cite: Ginski2016)" (main text)
- External data: Distance of 185 pc  
  > "at a distance of 185 pc (cite: Gaia-Collaboration2018)" (HD 97048.) [from Gaia Collaboration 2018 (cite: Gaia-Collaboration2018)]
- External data: SPHERE point-source detection limit ~2 MJup  
  > "resulting in a point source detection limit of $\approx$2 M$_\mathrm{Jup}$ (cite: Ginski2016)" (main text) [from Ginski et al. 2016 (cite: Ginski2016)]
- External data: Planet mass range 0.4-4 MJup from scattered light gap width  
  > "consistent with the planet mass range 0.4 and 4 M$_\mathrm{Jup}$ estimated from the width of the scattered light gap" (main text) [from Dong & Fung 2017 (cite: Dong2017)]
- Simulation/model as data: 3D phantom SPH gas+dust simulations with planets at 130 au of 1, 2, 3, 5 MJup, post-processed with mcfost  
  > "we performed a series of 3D global gas and multi-grain dust hydrodynamics simulations, where we embedded a planet on a circular orbit at 130 au with a mass of 1, 2, 3 and 5 M$_\mathrm{Jup}$" (main text)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: One round of phase self-cal on Nov 24 data, two rounds on the other two; solutions applied to line data  
  > "We performed one round of phase self calibration on the continuum data set observed November 24th, and two rounds on the other two data sets, and applied the self calibration solutions to the line data." (Observations and data reduction.)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs weighting (robust value not stated)  
  > "We imaged the visibilities at a 120 m s$^{-1}$ velocity spacing using Briggs weighing" (Observations and data reduction.)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Hanning smoothing; 120 m/s channel spacing  
  > "We imaged the visibilities at a 120 m s$^{-1}$ velocity spacing" (Observations and data reduction.)
- final beam: 0.11" x 0.07" at PA -38 deg  
  > "resulting in a beam size of 0.11” $\times$ 0.07” arcsec at a PA of -38$^\circ$." (Observations and data reduction.)
- final rms: 3.6 mJy/beam per channel  
  > "Typical RMS values obtained are 3.6 mJy/beam per channel for the combined data." (Observations and data reduction.)

### Inherited from earlier work

- Altitude of 13CO emitting layer measured with same procedure  
  > "Using the same procedure as in ref.(cite: Pinte2018a), we measured the altitude of the $^{13}$CO layer" (main text) [from Pinte et al. 2018 (cite: Pinte2018a)]
- 13CO freeze-out, photodissociation and photodesorption prescription  
  > "follow the prescription described in Appendix B of (cite: Pinte2018a) to account for freeze-out where T $< 20$ K" (3D modelling procedure.) [from Pinte et al. 2018 (cite: Pinte2018a)]
- Multi-grain dust algorithm in phantom  
  > "using the algorithm described in (cite: Hutchison2018; Ballabio2018)" (3D modelling procedure.) [from Hutchison et al. 2018; Ballabio et al. 2018]

### Not stated but needed to reproduce (our reading)

- Briggs robust value, cell and image size, and CLEAN threshold/masking
- CASA version and whether the pipeline or manual calibration was used
- Self-calibration solution intervals and reference datasets
- Method for extracting kink location and amplitude (done by eye?)
- Quantitative criterion for choosing the best-matching planet mass
- Rest frequency and systemic velocity adopted
- Disc inclination and PA adopted in models
- Fluffy-grain shift factor applied to SPH grain sizes

## Analysis recipe

1. **Image the 13CO and continuum data**: Self-calibrate and image visibilities at 120 m/s spacing with Briggs weighting  
  > "We imaged the visibilities at a 120 m s$^{-1}$ velocity spacing using Briggs weighing" (Observations and data reduction.)
   - software: CASA
   - fitting: _not stated_
   - validation: Kink present in all 3 individual executions and with/without continuum subtraction  
  > "The kink in CO emission discussed in this manuscript is present in all 3 individual executions and in both the continuum subtracted and non-subtracted images" (Observations and data reduction.)
2. **Locate the velocity kink and CO layer height**: Measure altitude of 13CO layer as in Pinte et al. 2018; infer planet position assuming it is in the midplane below the kink  
  > "Assuming that the planet is located in the disc midplane and exactly below the center of the velocity kink, it would be at a projected distance of 0.45$\pm$0.1"" (main text)
   - assumption: Planet in the midplane below the kink centre  
  > "Assuming that the planet is located in the disc midplane and exactly below the center of the velocity kink" (main text)
   - fitting: _not stated_
   - validation: _not stated_
3. **Run SPH gas+dust simulations with embedded planets**: phantom multi-grain SPH, 2 million particles, 11 dust bins 1.5625-1600 um, planets at 30 au (1 MJup) and 130 au (1, 2, 3, 5 MJup), 800 orbits  
  > "using 2 million SPH particles and following the dust fraction of particles of sizes ranging from 1.5625 to 1600 $\mu$m (11 bins total, each bin doubling the grain size)" (3D modelling procedure.)
   - software: phantom
   - parameter: Star 2.4 Msun, gas disc mass 1e-2 Msun, h/r=0.06 at 40 au, alpha_SS ~1e-3, inner/outer radius 40/700 au  
  > "The disc aspect ratio was set to 0.06 at 40 au" (3D modelling procedure.)
   - assumption: Distance 185 pc; vertically isothermal equation of state  
  > "We assume a central mass of 2.4 M$_\odot$ and a distance of 185 pc (cite: Gaia-Collaboration2018)." (3D modelling procedure.)
   - fitting: No formal fitting; planet mass compared by eye  
  > "As we do not aim to perform a detailed fitting of the data" (Impact of observational noise and $uv$ plane sampling.)
   - validation: Radiative-equilibrium phantom+mcfost runs show differences of only ~0.1 and 0.05 km/s in azimuthal and radial velocities  
  > "they remain limited to $\approx$0.1 and 0.05 km/s for the azimuthal and radial velocities, respectively." (Radiative-equilibrium hydrodynamics calculations.)
4. **Radiative transfer to synthesize continuum and 13CO maps**: mcfost Monte Carlo RT with Voronoi cells from SPH particles, LTE, Tgas=Tdust; maps at 50 m/s, binned and Hanning smoothed, convolved with the CLEAN beam  
  > "CO maps were generated at a spectral resolution of 50 m/s, binned at the observed resolution and Hanning smoothed to match the observed spectral resolution." (3D modelling procedure.)
   - software: mcfost
   - parameter: 13CO abundance 7e-7; turbulent velocity 50 m/s; star R=2.25 Rsun, Kurucz 10,000 K  
  > "We set the $^{13}$CO abundance to 7 10$^{-7}$" (3D modelling procedure.)
   - assumption: Dust mix 60% silicate, 15% amorphous carbon, hollow spheres (max void 0.8), dn/da ~ a^-3.5, dust-to-gas 1/100  
  > "assuming a power-law $\mathrm{d}n(a) \propto a^{-3.5}\mathrm{d}a$" (3D modelling procedure.)
   - fitting: _not stated_
   - validation: CASA ALMA simulator test shows kink shape not affected by uv sampling and noise  
  > "The shape of the velocity kink is not affected by observational effects" (Impact of observational noise and $uv$ plane sampling.)
5. **Compare models with data to estimate planet mass and dust Stokes number**: Visual comparison of channel maps and gap profile; mimic fluffy grains by shifting SPH grain sizes  
  > "The channel maps are best reproduced with an embedded planet of 2-3 M$_\mathrm{Jup}$, giving a velocity kink with amplitude matching the observations." (main text)
   - software: mcfost
   - fitting: _not stated_
   - validation: Moment-2 map shows no significant line broadening, ruling out the upper end of tested masses; consistent with SPHERE non-detection  
  > "This also rules out the upper end of the range tested in our simulations." (main text)

## Software

- **phantom** : 3D SPH gas+dust hydrodynamics  
  > "We performed a series of 3D global simulations using the phantom Smoothed Particle Hydrodynamics (SPH) code" (3D modelling procedure.)
- **mcfost** : Radiative transfer, temperature, continuum and CO maps  
  > "we used the mcfost Monte Carlo radiative transfer code" (3D modelling procedure.)
- **CASA** : ALMA simulator (modified) for synthetic visibilities and CLEANing  
  > "we also post-processed the 2 M$_\mathrm{Jup}$ model through a modified version of the CASA ALMA simulator." (Impact of observational noise and $uv$ plane sampling.)
- **splash** : Figure generation  
  > "Figures were generated with splash(cite: Price2007)" (Code availability)
- **pymcfost** : Figure generation  
  > "and pymcfost (<https://github.com/cpinte/pymcfost>)" (Code availability)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Altitude of 13CO layer near the kink (130 au) | 17 | 1 | au | 2 | we measured the altitude of the $^{13}$CO layer to be 17$\pm$1 au near the velocity kink (at a distance of 130 au) |
| Projected planet distance from star | 0.45 | 0.1 | arcsec | 2 | it would be at a projected distance of 0.45$\pm$0.1" and PA = $-55\pm$10$^\circ$ from the star. |
| Planet position angle | -55 | 10 | deg | 2 | PA = $-55\pm$10$^\circ$ from the star. |
| Planet mass preferred by kinematics | 2-3 | not stated | MJup | 5 | The channel maps are best reproduced with an embedded planet of 2-3 M$_\mathrm{Jup}$ |
| Stokes number of emitting dust grains | a few 1e-2 | not stated | dimensionless | 5 | dust grains dominating the thermal emission must have a Stokes number around a few $10^{-2}$ to reproduce the observed gap profile. |
| Channel velocity of strongest kink | 0.96 | not stated | km/s | 5 | the 0.96 km/s channel where the deviation is the strongest |

## Qualitative findings

- Velocity kink in the upper 13CO surface is coincident with the continuum gap; the opposite side shows no kink, excluding axisymmetric or large-scale mechanisms.  
  > "This excludes a large scale perturbation of the disc or an azimuthally symmetric mechanism." (main text)
- Emitting grains need a low Stokes number, suggesting fluffy aggregates  
  > "Another possibility is that dust grains of a few 100 microns or millimetres in size consist of fluffy aggregates" (main text)

## Claim tuples

- H: A localised kinematic deviation is spatially tied to the dust gap | E: 13CO channel maps compared with continuum in each channel | R: Kink located just above the continuum gap, at the same radius | F: The two features share a common origin | **supported**
- H: An embedded planet explains the kink, and which mass | E: SPH+RT models with 1, 2, 3, 5 MJup planets compared to channel maps | R: 2-3 MJup matches kink amplitude and velocity range; 1 too small, 5 too large | F: Planet of a few Jupiter masses at 130 au carves the gap | **supported**
- H: Compact grains explain the observed dust gap width | E: Compare model gap profiles using shifted grain sizes | R: Stokes number must be a few 1e-2, excluding compact grains in the models | F: Emitting grains may be fluffy aggregates | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Search for the dynamical effect of a planet on the gas disc, detectable in high spectral and spatial resolution line data  
  > "Our approach is to search for the dynamical effect of a planet on the surrounding gas disc." (main text)
- Alternative: Pressure bumps, gravitational instability and companion/flyby are rejected since they give axisymmetric or large-scale structures  
  > "While those pressure bumps produce deviations from Keplerian velocity, they are axisymmetric." (main text)
- How they decided it was enough: _not stated_
- Limitation (authors): No detailed fitting; models are qualitative comparisons  
  > "As we do not aim to perform a detailed fitting of the data" (Impact of observational noise and $uv$ plane sampling.)
- Caveat (inferred, ours): Planet mass from visual comparison with only four masses, no uncertainty
- Caveat (inferred, ours): Degeneracy with disc gas mass, viscosity and temperature structure not explored
- Caveat (inferred, ours): Compact-grain tension is resolved with an ad hoc grain-size shift
- Caveat (inferred, ours): Kink may be affected by line-of-sight cloud absorption or other non-planet effects; not tested

## Reproducibility

- Data public (paper): Raw data public in ALMA archive; reduced cubes on figshare (DOI 10.6084/m9.figshare.8266988)  
  > "Raw data is publicly available via the ALMA archive under project id 2016.1.00826.S." (Data availability)
- Products in archive: _not stated_
- Code: phantom public; mcfost available on request; splash and pymcfost open-source  
  > "mcfost is currently available under request and will be made open-source soon." (Code availability)
- Missing: Imaging parameters (robust, cell, mask)
- Missing: CASA version and calibration details
- Missing: Inclination, PA, systemic velocity of models
- Missing: Fluffy grain scaling details
- Data volume (inferred): ~50-100 GB raw for three Band 7 executions
- Score (inferred): 3/5, Public data and public phantom code, but imaging parameters are missing and the mass inference is qualitative.
- Rediscovery candidate: no, The main result relies on qualitative comparison with expensive hydrodynamic simulations, and few numbers are measured directly from the data.

## Links

- Method: Pinte et al. 2018 (cite: Pinte2018a) (Procedure for CO layer height and CO prescription)
- Method: Price et al. 2018 (cite: Price2018a) (phantom SPH code)
- Method: Pinte et al. 2006, 2009 (cite: Pinte06; Pinte09) (mcfost radiative transfer)
- Companion: Pinte et al. 2018 (cite: Pinte2018b) (Kinematic planet detection in HD 163296)
- Companion: van der Plas et al. 2017 (cite: van-der-Plas2017) (Previous ALMA observations of HD 97048)

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 53,
  "rate": 0.654
 },
 "evidence_ok": true
}
```
