# The Orbit of the Companion to HD 100453A: Binary-driven Spiral Arms in a Protoplanetary Disk

`2018ApJ...854..130W` | The Astrophysical Journal 2018 | first author: Wagner, Kevin | arXiv: 1801.03900 | DOI: 10.3847/1538-4357/aaa767

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks, stellar_physics
- Question: What is the orbit of the companion HD 100453B, and is it consistent with driving the spiral arms and truncating the disk of HD 100453A?  
  > "the orbit of these stars remained poorly understood, which prevented a proper treatment of the dynamical influence of the companion on the disk." (abstract)
- Target **HD 100453AB**: coordinates _not stated_; z/distance d=103±3 pc  
  > "HD 100453A (d=103$\pm$3 pc, (cite: GAIA1); $M_{\star}$=1.7M$_{\odot}$, (cite: Dominik2003))" (Introduction); distance from Gaia (GAIA1)  
  > "HD 100453A (d=103$\pm$3 pc, (cite: GAIA1); $M_{\star}$=1.7M$_{\odot}$, (cite: Dominik2003))" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00192.S
- bands: Band 6, Cycle 3  
  > "HD 100453 was observed on 2016 April 23 with ALMA Band 6 during Cycle 3" (2.4 ALMA 12CO Observations)
- frequencies and spectral setup: 1,920 channels centered at 230.529 GHz, 61 kHz widths (0.16 km/s, Hanning smoothed)  
  > "a baseband of 1,920 channels centered at 230.529 GHz with 61 kHz channel widths (0.16 km/s velocity resolution; Hanning smoothed)" (2.4 ALMA 12CO Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 12–460 m, 42 12-m antennas  
  > "forty-two 12 meter antennas were available, with baselines ranging from 12–460 meters." (2.4 ALMA 12CO Observations)
- angular resolution: 0.94" x 0.65", PA -67.8 deg  
  > "has a beam size of $0.94\ensuremath{''} \times 0.65\ensuremath{''}$ with PA of $-67.8^{\circ}$" (2.4 ALMA 12CO Observations)
- max recoverable scale: _not stated_
- sensitivity: mean rms 8.1 mJy/beam in signal-free channels  
  > "a mean rms of 8.1 mJy beam$^{-1}$ in signal-free channels" (2.4 ALMA 12CO Observations)
- time on source: ~13 minutes  
  > "The on-source time was $\sim$13 minutes." (2.4 ALMA 12CO Observations)
- observing dates: 2016 April 23  
  > "HD 100453 was observed on 2016 April 23 with ALMA Band 6" (2.4 ALMA 12CO Observations)
- pi or archival as stated: Public data, PI van der Plas  
  > "We utilized publicly available ALMA $^{12}$CO data" (abstract)
- Line: 12CO 2-1 (230.529 GHz (band center))
- Other facility **VLT/SPHERE**: Astrometry of HD 100453B at three epochs 2015-2016  
  > "We obtained data on three separate nights during 2015 and 2016 in IRDIFS and IRDIFS-Extended modes" (2.1 VLT/SPHERE Observations)
- Other facility **Magellan/MagAO Clio-2**: L' astrometry, 2017-02-17  
  > "We observed HD 100453 on February 17, 2017 using the Magellan Adaptive Optics System" (2.2 Magellan/MagAO Observations)
- Other facility **VLT/NACO**: Published 2003 and 2006 astrometry  
  > "We utilize two epochs of previously published data in our astrometric dataset." (2.3 Published VLT/NACO Data)
- External data: NACO separation and PA measurements (2003, 2006), recalibrated  
  > "We utilize these published separation and position angle measurements in our astrometric catalog" (2.3 Published VLT/NACO Data) [from (cite: Chen2006), (cite: Collins2009)]
- External data: Stellar mass 1.7 Msun  
  > "previous estimates of HD 100453’s mass (cite: Dominik2003) and distance (cite: GAIA1)" (3.2 CO 2–1 Modelling) [from (cite: Dominik2003)]
- Simulation/model as data: PEnGUIn hydrodynamic + HOCHUNK3D H-band scattered-light models at inclinations 25, 30, 35 deg  
  > "We reproduce the model three times with an inclination of $25^\circ, 30^\circ$, and $35^\circ$ from face-on" (3.3 Hydrodynamic and Near-Infrared Radiative Transfer Modelling)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA  
  > "The data were calibrated using the ALMA pipeline in the `CASA` package." (2.4 ALMA 12CO Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1107-4449 (bandpass and flux); J1132-5606 gain  
  > "J1107-4449 was used as the bandpass and flux calibrator, and J1132-5606 was used as the the gain calibrator." (2.4 ALMA 12CO Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN  
  > "we imaged the $^{12}$CO 2–1 data using the CLEAN routine." (2.4 ALMA 12CO Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting, 0.2 km/s channels  
  > "Imaging was done in 0.2 km/s channels using natural weighting to enhance sensitivity in the channel maps." (2.4 ALMA 12CO Observations)
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
- final beam: 0.94" x 0.65", PA -67.8 deg  
  > "has a beam size of $0.94\ensuremath{''} \times 0.65\ensuremath{''}$ with PA of $-67.8^{\circ}$" (2.4 ALMA 12CO Observations)
- final rms: _not stated_

### Inherited from earlier work

- CO disk modelling procedure of fitting synthetic channel maps  
  > "We follow the modelling procedure outlined in (cite: Wu2017) to fit our ALMA channel maps" (3.2 CO 2–1 Modelling) [from (cite: Wu2017)]
- Orbit-fitting grid search and bootstrapping  
  > "We employ the grid-search and bootstrapping method of orbit-fitting presented in (cite: Wagner2016)." (3.1 Orbital Modelling) [from (cite: Wagner2016)]
- Hydrodynamic plus radiative transfer strategy  
  > "following the strategy in (cite: Dong2016b)" (3.3 Hydrodynamic and Near-Infrared Radiative Transfer Modelling) [from (cite: Dong2016b)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- CLEAN threshold, mask, image size and cell size
- Whether continuum was subtracted and which channels were line-free
- Priors ranges for MCMC parameters and walker/step numbers
- Fixed parameters of the CO model such as outer radius, flaring, and CO depletion
- Initial disk mass and parameters of hydrodynamic simulation beyond h/r and alpha

## Analysis recipe

1. **Fit orbit to astrometry**: Grid search with chi-squared minimization and bootstrapping with Gaussian noise on six epochs  
  > "We constructed a grid of models and performed a chi-squared minimization to find the best-fit model, while keeping the mass of the system fixed at 1.9 M$_{\odot}$." (3.1 Orbital Modelling)
   - software: custom IDL scripts
   - parameter: 25,265 bootstrap trials; 46,656 grid combinations; seven iterations with grid halved  
  > "The distribution of orbital parameters shown in §4.2 were assembled by repeating the procedure for 25,265 trials" (3.1 Orbital Modelling)
   - assumption: System mass fixed at 1.9 Msun  
  > "keeping the mass of the system fixed at 1.9 M$_{\odot}$" (3.1 Orbital Modelling)
   - fitting: Chi-squared grid minimization with bootstrapped noise  
  > "performed a chi-squared minimization to find the best-fit model" (3.1 Orbital Modelling)
   - validation: Acknowledged six-parameter model overfits six data points; bootstrapping mitigates  
  > "our six-parameter model[^6] is over-fitting our six available data points" (4.2 Orbital Parameters of HD 100453AB)
2. **Fit disk kinematics to ALMA CO visibilities**: RADMC-3D synthetic 12CO 2-1 channel maps Fourier transformed and fit to visibilities with MCMC  
  > "Those synthetic channel maps are Fourier Transformed and fit directly to the visibilities using the MCMC fitting package `emcee`" (3.2 CO 2–1 Modelling)
   - software: RADMC-3D, emcee
   - parameter: Free: M_disk, r_c, gamma, T0, q, xi, v_sys, inclination, PA  
  > "the density, temperature, and velocity structure of the system are described by the following parameters: $M_{\rm disk}$, $r_{\rm c}$, $\gamma$, $T_0$, $q$, $\xi$, and $v_{sys}$." (3.2 CO 2–1 Modelling)
   - assumption: M*=1.7 Msun, d=103 pc, X_CO=1e-4, mu=2.37, inner radius 0.1 AU, Keplerian, vertically isothermal, single plane  
  > "Here we fix the stellar mass to a value of $M_* = 1.7$ $M_{\odot}$ and the distance to a value of $d = 103$ pc" (3.2 CO 2–1 Modelling)
   - fitting: emcee with uniform priors for all parameters  
  > "with uniform priors for all parameters" (3.2 CO 2–1 Modelling)
   - validation: Compared moment maps and residuals; inclination consistent with NIR estimates  
  > "is consistent with the independent measurements from the NIR images (Figure 5)" (4.3.2 ALMA Disk Kinematic Modelling)
3. **Simulate companion-driven spirals**: PEnGUIn 3D hydrodynamics for 100 orbits then HOCHUNK3D H-band images at 25, 30, 35 deg  
  > "The three-dimensional disk density profile was computed for one-hundred companion orbits" (3.3 Hydrodynamic and Near-Infrared Radiative Transfer Modelling)
   - software: PEnGUIn, HOCHUNK3D
   - parameter: Circular orbit, a=100 AU, mass ratio 1:10, h/r=0.15, alpha=1e-3  
  > "In our simulation we parametrized the disk to have $h/r$ = 0.15 and $\alpha$ = 10$^{-3}$" (5.1 Effects on the Disk Structure from HD 100453B)
   - assumption: ISM-like grains, Henyey-Greenstein scattering  
  > "The anisotropic scattering phase function is approximated using the Henyey-Greenstein function" (3.3 Hydrodynamic and Near-Infrared Radiative Transfer Modelling)
   - fitting: _not stated_
   - validation: Qualitative comparison with observed spirals  
  > "the companion induces a prominent two-armed spiral structure that is qualitatively similar to the observed spirals in HD 100453" (4.4 Hydrodynamic + Radiative Transfer Simulations)

## Software

- **CASA** : ALMA pipeline calibration and CLEAN imaging  
  > "The data were calibrated using the ALMA pipeline in the `CASA` package." (2.4 ALMA 12CO Observations)
- **RADMC-3D** : synthetic 12CO channel maps  
  > "We use the 3D radiative transfer modelling package `RADMC-3D` (cite: Dullemond2012)" (3.2 CO 2–1 Modelling)
- **emcee** : MCMC fit to visibilities  
  > "using the MCMC fitting package `emcee` (cite: FM13)" (3.2 CO 2–1 Modelling)
- **PEnGUIn** : 3D hydrodynamic simulation  
  > "We utilize the three-dimensional hydrodynamic package, `PEnGUIn` (cite: Fung2015)" (3.3 Hydrodynamic and Near-Infrared Radiative Transfer Modelling)
- **HOCHUNK3D** : scattered light radiative transfer  
  > "the radiative transfer package, `HOCHUNK3D` (cite: Whitney2013)" (3.3 Hydrodynamic and Near-Infrared Radiative Transfer Modelling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk inclination from CO | 27.6 | 0.2 | deg | 2 | $i_{Disk}$ ($^{\circ}$)  /        27.6         /         0.2 |
| Disk position angle | 55.0 | 0.5 | deg | 2 | $PA$ ($^{\circ}$)     /        55.0         /         0.5 |
| Systemic velocity | 5.25 | 0.01 | km/s | 2 | $v_{sys}$ (km/s)     /        5.25         /        0.01 |
| Disk gas mass (model) | 7.0e-6 | 1.0e-6 | Msun | 2 | $M_{Disk}$ (M$_{\odot}$) / 7.0$\times 10^{-6}$ / 1.0$\times 10^{-6}$ |
| Orbit semi-major axis | 1.06 | 0.09 | arcsec | 1 | *a*=1$\ensuremath{''}$06$\pm0.09\ensuremath{''}$ |
| Orbit eccentricity | 0.17 | 0.07 | dimensionless | 1 | *e*$=0.17\pm0.07$ |
| Orbit inclination | 32.5 | 6.5 | deg | 1 | *i*=$32.5^{\circ}\pm6.5^\circ$ |

## Qualitative findings

- Companion drives the two-armed spiral and truncates the circumprimary disk; star rotation, outer disk and companion share angular momentum direction  
  > "We find that the spiral structure and truncation of the circumprimary disk in HD 100453 are consistent with a companion-driven origin." (abstract)

## Claim tuples

- H: Is the companion's orbit co-planar with the outer disk? | E: Orbit fit to six astrometric epochs and ALMA CO kinematic modelling | R: Orbit i=32.5±6.5 deg; disk i~28 deg | F: Orbit and outer disk roughly co-planar | **supported**
- H: Does the companion drive the spiral arms? | E: Hydrodynamic and radiative transfer simulations at 25-35 deg | R: Two-armed spiral qualitatively matches observations | F: Companion-driven origin consistent; other mechanisms not necessary | **supported**

## Reasoning

- Why this data: Public ALMA CO data used to measure the outer disk inclination  
  > "We also present disk kinematic modelling of publicly available *Atacama Large Millimeter/Sub-millimeter Array* (ALMA) CO data to measure the inclination of the disk" (1 Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Simple model cannot capture inner structures or warp; uncertainties exclude model assumptions  
  > "our simple model cannot capture all of the disk features that result in the observed CO emission profile." (4.3.2 ALMA Disk Kinematic Modelling)
- Caveat (inferred, ours): Disk inclination relies on a simple unwarped model with tiny formal errors
- Caveat (inferred, ours): Orbit fit uses six points for six parameters
- Caveat (inferred, ours): Hydro comparison is only qualitative

## Reproducibility

- Data public (paper): Publicly available ALMA data  
  > "We utilized publicly available ALMA $^{12}$CO data" (abstract)
- Products in archive: _not stated_
- Missing: Imaging parameters and CASA version
- Missing: MCMC setup
- Missing: Custom IDL code for astrometry
- Data volume (inferred): ~10-50 GB (single 13-minute Band 6 execution)
- Score (inferred): 3/5, ALMA data are public and the model is described, but CLEAN, MCMC setup and code details are missing.
- Rediscovery candidate: no, ALMA role is minor and fitting setup is incomplete; main orbital results rely on non-ALMA data.

## Links

- Method: (cite: Wu2017) (CO disk modelling procedure)
- Method: (cite: Wagner2016) (Orbit fitting method)
- Companion: van der Plas et al, in prep (More detailed ALMA modelling and higher resolution data)
- Companion: (cite: Dong2016a) (Earlier simulations of spirals)

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 48,
  "rate": 0.649
 },
 "evidence_ok": true
}
```
