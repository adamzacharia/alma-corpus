# A Major Asymmetric Dust Trap in a Transition Disk

`2013Sci...340.1199V` | Science 2013 | first author: van der Marel, Nienke | arXiv: 1306.1768 | DOI: 10.1126/science.1236770

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Is the dust in the transition disk around Oph IRS 48 distributed asymmetrically relative to the gas and small grains, as expected for a dust trap in a vortex?  
  > "The difference in distribution of big grains versus small grains/gas can be modeled with a vortex-shaped dust trap triggered by a companion." (abstract)
- Target **Oph IRS 48 (WLY 2-48)**: coordinates J2000 RA=16 27 37.18, Dec=-24 30 35.3  
  > "The A0 star IRS 48 a.k.a. WLY 2-48 (J2000 RA=16 27 37.18, Dec=-24 30 35.3) is located in the ρ Ophiuchi star formation region at a distance of 120 parsec" (Materials and Methods); z/distance 120 pc  
  > "The A0 star IRS 48 a.k.a. WLY 2-48 (J2000 RA=16 27 37.18, Dec=-24 30 35.3) is located in the ρ Ophiuchi star formation region at a distance of 120 parsec" (Materials and Methods); distance from Loinard et al. 2008 (ref 31)  
  > "The A0 star IRS 48 a.k.a. WLY 2-48 (J2000 RA=16 27 37.18, Dec=-24 30 35.3) is located in the ρ Ophiuchi star formation region at a distance of 120 parsec" (Materials and Methods)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 9 (0.44 mm, 685 GHz)  
  > "The ALMA observations of IRS 48 were taken using Band 9 in Early Science Cycle 0 using the extended configuration." (Materials and Methods)
- frequencies and spectral setup: 4 spectral windows centered at 674.00, 678.84, 691.47, 693.88 GHz; 3840 channels each, 488 kHz spacing, 0.21 km/s resolution  
  > "The spectral setup consisted of four spectral windows, centered at 674.00, 678.84, 691.47 and 693.88 GHz." (Materials and Methods); "Each spectral window consists of 3840 channels, a channel separation of 488 kHz and thus a bandwidth of 1875 MHz." (Materials and Methods)
- continuum bandwidth: ~6.5 GHz, mean frequency 684.55 GHz  
  > "The total bandwidth of the continuum is ~6.5 GHz, with a mean frequency of 684.55 GHz." (Materials and Methods)
- arrays: _not stated_
- configurations: Cycle 0 extended configuration; 18 to 21 antennas  
  > "Between these three execution blocks, 18 to 21 antennas were used with baselines up to 390 meter." (Materials and Methods)
- baselines: up to 390 m  
  > "Between these three execution blocks, 18 to 21 antennas were used with baselines up to 390 meter." (Materials and Methods)
- angular resolution: 0.32" × 0.21", PA 96°  
  > "providing a synthesized beam of 0.32" × 0.21" at a position angle of 96º." (Materials and Methods)
- max recoverable scale: spatial filtering for >500 AU  
  > "For the ALMA data, the spatial filtering occurs for >500 AU" (Materials and Methods)
- sensitivity: continuum rms 0.82 mJy/beam; line ~18 mJy/beam per 1 km/s bin  
  > "The RMS noise level is 0.82 mJy/beam for the continuum and ~18 mJy/beam per 1 km s [-1 ] bin for the line data." (Materials and Methods)
- time on source: three execution blocks of 1.7 hours each  
  > "Data were taken on June 6th and July 17th 2012 in three execution blocks of 1.7 hours each" (Materials and Methods)
- observing dates: 6 June and 17 July 2012  
  > "Data were taken on June 6th and July 17th 2012 in three execution blocks of 1.7 hours each" (Materials and Methods)
- pi or archival as stated: _not stated_
- Line: 12CO J=6-5 (not stated)
- Line: C17O J=6-5 (not stated)
- Other facility **VLT-VISIR**: 18.7 μm imaging of small-grain ring  
  > "A ring-like structure peaking at ~55 AU radius was found by spatially resolved 18.7 μm imaging of the dust continuum with the Very Large Telescope (VLT)-VISIR instrument" (Materials and Methods)
- Other facility **VLT-CRIRES**: 4.7 μm CO ro-vibrational spectra (hot gas ring at ~30 AU)  
  > "Previous information on the gas in the IRS 48 disk comes from VLT-CRIRES spectra of the CO ro-vibrational transition at 4.7 μm" (Materials and Methods)
- Other facility **SMA**: 0.85 mm fluxes (and 1.3 mm) used for spectral slope  
  > "Interferometric imaging with the SubMillimeter Array (SMA) in the very extended configuration at 0.85 mm (345 GHz) revealed a single elliptical structure" (Materials and Methods)
- External data: Submillimeter fluxes at 230 and 345 GHz (50 and 160 mJy) used for beta  
  > "(50, 160 and 950 mJy _(33),_ the 685 GHz flux density derived in this work)" (Materials and Methods) [from Brown et al. 2012 (ref 33)]
- External data: Dust mass opacity at 685 GHz ≈ 9/a_max[mm] cm2/g  
  > "For a dust-size distribution N(a) ~ a^-3.5 and amorphous silicate spheres, the dust mass opacity is" (Materials and Methods, Dust mass) [from Draine 2006 (ref 15)]
- External data: Distance 120 pc  
  > "located in the ρ Ophiuchi star formation region at a distance of 120 parsec _(31)_" (Materials and Methods) [from Loinard et al. 2008 (ref 31)]
- Simulation/model as data: FARGO 2D hydro simulation (10 MJup companion at 20 AU, alpha=1e-4) plus dust evolution and azimuthal redistribution, imaged in CASA to produce simulated ALMA map  
  > "The resulting continuum emission is imaged using CASA (v. 3.4.0) using the same configurations as in the actual ALMA observations." (Materials and Methods)

## Processing

### Calibration

- pipeline or manual: Manual reduction with CASA 3.4  
  > "Reduction and calibration of the data was done using the Common Astronomy Software Application (CASA) version 3.4." (Materials and Methods)
- casa version: CASA 3.4  
  > "Reduction and calibration of the data was done using the Common Astronomy Software Application (CASA) version 3.4." (Materials and Methods)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (shortest ~30% of baselines); bandpass 3c279  
  > "The bandpass was calibrated using quasar 3c279 and fluxes were calibrated against Titan." (Materials and Methods)
- flux scale uncertainty: <20% overall calibration uncertainty  
  > "In the end the overall calibration uncertainty is less than 20%." (Materials and Methods)
- self calibration: Phase self-calibration on IRS 48 continuum using unselfcalibrated continuum as model; 40% S/N gain  
  > "This resulted in a net gain of 40% in S/N." (Materials and Methods)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The image conversion of the continuum and line data was done using natural weighting" (Materials and Methods)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Continuum: elliptical mask from unselfcalibrated 3σ shape padded by half a beam; lines: rectangular mask extending 0.24'' around emission peaks, adapted per channel  
  > "extending 0.24'' in all directions to cover most assumed emission." (Materials and Methods)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Continuum from line-free channels of all four spws, edge channels and strong CO 6-5 channels flagged  
  > "flagging the edge channels and the channels containing the strong CO 6-5 emission." (Materials and Methods)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.32" × 0.21", PA 96°  
  > "providing a synthesized beam of 0.32" × 0.21" at a position angle of 96º." (Materials and Methods)
- final rms: 0.82 mJy/beam continuum  
  > "The RMS noise level is 0.82 mJy/beam for the continuum" (Materials and Methods)

### Inherited from earlier work

- Dust opacity and spectral-index interpretation of beta  
  > "This low value of _β << β_ ISM ≈ 1.7 is indicative of grain growth _(15)_ ." (Materials and Methods) [from Draine 2006 (ref 15)]
- Vortex dust-trap azimuthal redistribution (sinusoidal perturbation)  
  > "we now redistribute at each radius the dust using a sinusoidal perturbation _(9)_ with a gas contrast of 3" (Materials and Methods) [from Birnstiel et al. 2013 (ref 9)]
- Dust evolution code  
  > "The dust evolution code ( _39_ ) is run on this profile" (Materials and Methods) [from ref 39 as cited]

### Not stated but needed to reproduce (our reading)

- CLEAN threshold, number of iterations, cell and image size
- Self-calibration solution interval and reference antenna
- Exact channel ranges flagged as CO-contaminated
- Rest frequencies adopted for lines
- Details of the generic radiative transfer model giving the 60 K dust temperature
- Dust evolution model parameters (fragmentation velocity, etc.)
- How the model image was sampled (uv coverage, noise) for Fig. 2
- Fitting method and error derivation for the arc profile

## Analysis recipe

1. **Calibrate and image continuum and CO lines**: CASA calibration with Titan/3c279/J1625-254, phase self-cal on continuum, natural-weighted CLEAN with masks  
  > "The calibration was improved by calibrating these fluctuations on the continuum of IRS 48 itself." (Materials and Methods)
   - software: CASA
   - parameter: natural weighting; beam 0.32" × 0.21"  
  > "The image conversion of the continuum and line data was done using natural weighting" (Materials and Methods)
   - fitting: _not stated_
   - validation: Different clean masks compared on selfcal and non-selfcal images; no structural differences  
  > "different sizes and shapes of clean masks were compared to the result seen in the main paper." (Materials and Methods)
2. **Fit morphology of dust crescent**: Fourth-power Gaussian-like radial and azimuthal profile convolved with the beam, fit to continuum  
  > "assuming a fourth power Gaussian-like distribution in both radial and azimuthal direction" (Materials and Methods)
   - parameter: i=50°, PA=97°, center from CO Keplerian model  
  > "Applying the inclination of _i_ =50º, position angle of 97º (measured from the CO data; North to East)" (Materials and Methods)
   - fitting: Best fit: Rc=63±8 AU, Rw=18±2 AU, φc=95±10°, φw=50±5°  
  > "the best fit to the continuum data was found for R_c = 63 (± 8) AU, R_w = 18 (± 2) AU," (Materials and Methods, Morphology of the continuum emission)
   - validation: _not stated_
3. **Derive dust mass and spectral index**: Optically thin-ish emission with B_ν(Tdust) and opacity; beta from power-law fit to 230, 345, 685 GHz fluxes; kappa=9/a_max cm2/g  
  > "The value of _β_ is estimated by making a power law fit to the (sub)millimeter fluxes at 230, 345 and 685 GHz" (Materials and Methods)
   - parameter: emission area 2544 AU2; total flux 950 mJy; tau=0.43  
  > "For the total flux density of 950 mJy at 685 GHz, we obtain _τ_ _685 GHz_ _=_ 0.43." (Materials and Methods)
   - assumption: Dust temperature 60 K; dust size distribution N(a)~a^-3.5; amorphous silicate spheres; gas/dust 100  
  > "For a dust-size distribution _N(a) ~ a_ _[-3.5]_ and amorphous silicate spheres" (Materials and Methods)
   - fitting: _not stated_
   - validation: Flux loss from spatial filtering argued <20%  
  > "so flux loss by spatial filtering will be even less than 20%." (Materials and Methods)
4. **Analyze CO kinematics and gas mass**: Keplerian analysis of 12CO 6-5 wings for gas hole radius and source velocity; C17O 6-5 flux converted to gas mass for T=50-200 K  
  > "Integrating over the channels with significant C [17] O detections (962 mJy km s [-1] ) and calculating the mass for an average gas temperature between 50 and 200 K" (Materials and Methods)
   - parameter: 2 Msun star, i=50°  
  > "in agreement with gas at 20 AU in Keplerian rotation around a 2 M Sun star at an inclination of 50º." (Materials and Methods)
   - assumption: 12CO/C17O=2500; H2/12CO=1.2e4; all gas in H2  
  > "with _X_ the relative abundances (2500 for [12] CO/C [17] O, 1.2∙10 [4] for H 2 / [12] CO)" (Materials and Methods)
   - fitting: _not stated_
   - validation: Folded spectrum over source velocity to confirm symmetry  
  > "Folding the full spectrum over the source velocity of 4.55 km s [-1] also shows this symmetry (Fig. S3B)." (Materials and Methods)
5. **Model vortex dust trap and compare**: FARGO 2D hydro with 10 MJup planet at 20 AU, dust evolution on radial gas profile, azimuthal redistribution with gas contrast 3, opacity-based imaging with CASA  
  > "The used parameters are: stellar mass _M_ star = 2 M Sun, companion mass _M_ _p_ _=_ 10 M Jup, companion orbital radius _r_ _p_ _=_ 20 AU and turbulence _α_ _t_ _=_ 10 [-4] ." (Materials and Methods)
   - software: FARGO, CASA
   - parameter: grid 512×757; h/r=0.05; flaring index 0.25; grain sizes 1 μm–10 cm; rho_s=0.8 g/cm3  
  > "we consider a grid of grain size from 1 μm to 10 cm and an intrinsic dust density _ρ_ _s_ _=_ 0.8 g cm [-3] ." (Materials and Methods)
   - assumption: Low optical depth, spherical magnesium-iron-silicate grains  
  > "assuming low optical depth and spherical magnesium-iron-silicate grains _(44)._" (Materials and Methods)
   - fitting: _not stated_
   - validation: Model morphology and contrast compared to observed; model trap closer and narrower, higher peak  
  > "The model does not predict the exact same radial extent as the dust trap in IRS 48" (Materials and Methods)

## Software

- **CASA** 3.4: Calibration, imaging of ALMA data and of the simulated model  
  > "Reduction and calibration of the data was done using the Common Astronomy Software Application (CASA) version 3.4." (Materials and Methods)
- **FARGO** : 2D hydrodynamic simulation of planet-carved cavity and vortex  
  > "we use the two-dimensional hydrodynamical code FARGO _(39)_ ." (Materials and Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum rms | 0.82 | not stated | mJy/beam | 1 | The RMS noise level is 0.82 mJy/beam for the continuum |
| Total continuum flux at 685 GHz | 950 | <20% calibration | mJy | 1 | The total continuum flux is 950 mJy. |
| Peak S/N and north/south contrast | ~390; at least 130 | not stated | dimensionless | 1 | The peak emission has a very high signal-to-noise ratio of ~390 and the contrast with the upper limit on the opposite side of the ring is at least a factor of 130. |
| Spectral slope alpha | 2.67 | 0.25 | dimensionless | 3 | is only 2.67 ± 0.25 ( _F_ _ν_ ∝ _ν_ _[α]_ ) |
| Dust opacity index beta | 0.67 | 0.25 | dimensionless | 3 | we obtain _β_ = 0.67 ± 0.25. |
| Crescent radial center Rc | 63 | 8 | AU | 2 | _R_ _c_ = 63 (± 8) AU |
| Crescent elongation | ~3.1 | 0.6 | dimensionless | 2 | The elongation of our dust trap is ~3.1 (± 0.6) with the derived parameters. |
| Dust mass (lower limit, a_max>4 mm, T=60 K) | 9 | not stated | Earth masses | 3 | With _a_ max - 4 mm this yields a lower limit of the dust mass of 9 M Earth . |
| Gas surface density drop radius | ~25 | 5 | AU | 4 | a significant drop of the gas surface density inside of ~25 ± 5 AU |
| Gas mass from C17O | 19-27 | not stated | MJup | 4 | we find a total gas mass between 19 and 27 M Jup . |
| LSR source velocity | 4.55 | not stated | km/s | 4 | The Local Standard of Rest source velocity is derived from the symmetry of the [12] CO 6-5 profile as 4.55 km s [-1] . |

## Qualitative findings

- Millimeter dust is concentrated in a crescent on one side while gas and micron-sized dust trace rings centered on the star  
  > "whereas both the mid-infrared image (micrometer-sized dust) and the gas traced by the carbon monoxide 6-5 rotational line suggest rings centered on the star." (abstract)

## Claim tuples

- H: Is the mm dust in IRS 48 asymmetrically trapped while gas and small grains form full rings? | E: ALMA Band 9 continuum and CO 6-5 compared with VISIR 18.7 μm | R: Crescent with contrast >130 spanning ~100° at 45-80 AU; CO Keplerian down to 20 AU | F: Large grains are trapped in an asymmetric structure unlike gas/small grains | **supported**
- H: Can a companion-induced vortex explain the dust trap? | E: FARGO plus dust evolution model imaged with ALMA configuration | R: 10 MJup planet at 20 AU yields long-lived vortex and high azimuthal dust contrast, but peak is higher and trap narrower/closer | F: Companion-triggered vortex is the most viable scenario | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Simultaneous line and continuum in one dataset gives precise stellar position and gas-dust relative location  
  > "the combined ALMA observations of line and continuum within the same dataset is crucial for accurate interpretation." (Materials and Methods)
- Alternative: Photoevaporation, dead zone, gravitational instability, planet collision remnants and debris-disk clumps considered and judged less likely  
  > "we discuss other scenarios that could potentially lead to this kind of asymmetry and explain why they are less likely" (Materials and Methods)
- How they decided it was enough: _not stated_
- Limitation (authors): Azimuthal gas density variations cannot be constrained by current data  
  > "The amount of variation cannot be constrained by the current data set." (Materials and Methods)
- Caveat (inferred, ours): Dust mass depends on assumed 60 K temperature from generic model and a_max
- Caveat (inferred, ours): Companion mass/location only loosely constrained and not reproduced exactly by model
- Caveat (inferred, ours): CO 6-5 optically thick and foreground absorption limit gas azimuthal constraints

## Reproducibility

- Data public (paper): Data archived at alma-allegro.nl and to be public in ALMA archive  
  > "the full project data (2011.0.00635.SSB) will be publicly available at the ALMA Science Data Archive" (Acknowledgments)
- Products in archive: _not stated_
- Missing: CLEAN parameters and self-cal details
- Missing: Dust evolution model parameters and radiative transfer model details
- Data volume (inferred): ~50-100 GB raw (three Band 9 execution blocks with 4 spws of 3840 channels)
- Score (inferred): 3/5, Data public and calibration/imaging described, but key imaging and modelling parameters are missing; main results numeric.
- Rediscovery candidate: yes, Public Cycle 0 data, described recipe, numeric continuum fits and masses can be redone.

## Links

- Companion: Casassus et al. 2013 (ref 10) (Earlier ALMA dust asymmetry in another disk)
- Companion: Birnstiel et al. 2013 (ref 9) (Dust trapping model in vortices)

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00635.S"
 ],
 "codes_printed_but_missing": [
  "2011.0.00635.SSB"
 ],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 59,
  "rate": 0.728
 },
 "evidence_ok": true
}
```
