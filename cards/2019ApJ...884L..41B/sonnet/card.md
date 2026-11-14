# An Ideal Testbed for Planet-Disk Interaction: Two Giant Protoplanets in Resonance Shaping the PDS 70 Protoplanetary Disk

`2019ApJ...884L..41B` | The Astrophysical Journal Letters 2019 | first author: Bae, Jaehan | arXiv: 1909.09476 | DOI: 10.3847/2041-8213/ab46b0

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks, exoplanets
- Question: Can 2D hydrodynamic simulations of two growing planets in the PDS 70 disk reproduce the observed disk features (cavity, sub-mm ring, resonance, CPD emission)?  
  > "PDS 70 offers an ideal testbed for planet-disk interaction studies." (abstract)
- Target **PDS 70**: coordinates _not stated_; z/distance 113 pc  
  > "the $5.4$ Myr-old, K7 pre-main sequence star PDS 70" (1 INTRODUCTION); "Adopting the distance $d=113$ pc (cite: gaia16; gaia18)" (4.2 Circumplanetary Disks); distance from Gaia (cite: gaia16; gaia18)  
  > "the $5.4$ Myr-old, K7 pre-main sequence star PDS 70" (1 INTRODUCTION); "Adopting the distance $d=113$ pc (cite: gaia16; gaia18)" (4.2 Circumplanetary Disks)

## Data provenance

- ALMA projects: 2015.1.00888.S, 2017.A.00006.S
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
- External data: Observed 855 micron continuum image and CPD continuum flux (~100 uJy) of PDS 70  
  > "far too small to explain the observed continuum flux of $\sim100~\mu$Jy (cite: isella19)" (4.2 Circumplanetary Disks) [from (cite: isella19)]
- External data: Sub-mm continuum ring at ~74 au, gas pressure/CO constraints, stellar mass 0.85 Msun, disk gas mass model  
  > "Adopting a stellar mass of $0.85~M_\odot$ (cite: keppler19)" (2.1 Initial Gas Disk) [from (cite: keppler19)]
- External data: Planet accretion rates from Halpha 1e-8 to 1e-7 MJup/yr  
  > "consistent with the estimates based on H$\alpha$ observations (cite: wagner18; haffert19)" (2.2 Planets) [from (cite: wagner18; haffert19)]
- Simulation/model as data: 2D locally isothermal Dusty FARGO-ADSG simulations with Lagrangian test particles, plus RADMC-3D MCRT simulated continuum images  
  > "We carry out two-dimensional, locally isothermal hydrodynamical simulations using the Dusty FARGO-ADSG code (cite: baruteau19)." (2.3 Hydrodynamic Simulations)

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

- Disk gas mass model and stellar mass  
  > "similar to the model used in (cite: keppler19)" (2.1 Initial Gas Disk) [from (cite: keppler19)]
- Gas accretion onto planets prescription  
  > "following the approach presented in (cite: kley99) and (cite: durmann17)" (2.2 Planets) [from (cite: kley99), (cite: durmann17)]
- Turbulent diffusion of particles  
  > "following the method presented in (cite: charnoz11)" (2.3 Hydrodynamic Simulations) [from (cite: charnoz11)]

### Not stated but needed to reproduce (our reading)

- Details of the ALMA observed image used in Figure 5 (beam, rms, calibration), not described
- Beam and noise used to convolve the simulated images
- Inclination and position angle used for the simulated images
- Dust opacity file / Jena database version

## Analysis recipe

1. **Set up disk temperature**: Iterate RADMC-3D Monte Carlo radiative transfer with hydrostatic density until the temperature changes by less than 1%  
  > "does not vary more than $1\%$ at each radius from the previous iteration" (Initial Disk Temperature)
   - software: RADMC-3D
   - parameter: 1e9 photon packages; f=0.1; L*=0.35 Lsun  
  > "In each Monte Carlo calculation we use $10^9$ photon packages." (Initial Disk Temperature)
   - fitting: _not stated_
   - validation: _not stated_
2. **Run hydrodynamic planet-disk simulations**: 2D locally isothermal gas plus Lagrangian dust test particles, 2 Myr, PDS 70c mass 2.5, 5 or 10 MJup, plus a b-only run  
  > "We test three different masses for PDS 70c: 2.5, 5, and 10 $M_{\rm Jup}$." (2.2 Planets)
   - software: Dusty FARGO-ADSG
   - parameter: alpha=1e-3; grid 672x936; domain 2.2-198 au  
  > "We adopt 672 logarithmically-spaced grid cells in the radial direction and 936 uniformly-spaced grid cells in the azimuthal direction." (2.3 Hydrodynamic Simulations)
   - assumption: Dust bulk density 1.26 g cm-3; particle sizes 0.1 um to 1 mm; dust-to-gas 2.5% between 50 and 100 au  
  > "We assume a dust bulk density of $1.26~{\rm g~cm}^{-3}$" (2.3 Hydrodynamic Simulations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Produce simulated continuum images and compare with ALMA**: MCRT on the t=0.6 Myr density with Hill spheres filled, size-distribution opacities, Henyey-Greenstein scattering  
  > "Simulated continuum images are produced considering both absorption and anisotropic scattering using the Henyey-Greenstein approximation." (Simulated Continuum Observation)
   - software: RADMC-3D
   - assumption: Grains 30% silicate and 70% water ice; size distribution exponent -3.5; 0.1 um to 1 mm  
  > "We assume that grains are composed of $30~\%$ silicate matrix and $70~\%$ water ice" (Simulated Continuum Observation)
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate CPD dust mass and flux analytically**: Steady-state M_dust,CPD = Mdot_acc * tau_vis; optically thin flux with kappa ~2 cm2/g  
  > "With an opacity of $\sim 2~{\rm cm}^2~{\rm g}^{-1}$ for sub-$\mu$m grains at $855~\mu$m" (4.2 Circumplanetary Disks)
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Dusty FARGO-ADSG** : 2D hydrodynamic simulations with dust test particles  
  > "`Dusty FARGO-ADSG` (cite: baruteau19), `RADMC-3D` (cite: radmc3d)" (Software)
- **RADMC-3D** : Monte Carlo radiative transfer for temperature and simulated images  
  > "we iterate Monte Carlo radiative transfer (MCRT) calculations using RADMC-3D (cite: radmc3d)" (2.1 Initial Gas Disk)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk temperature fit at 22 au | 44 | not stated | K | 1 | \bar{T}(R) = 44~{\rm K} \left( {R \over 22~{\rm au}} \right)^{-0.24} |
| Sub-mm particle trap radius, two-planet models (Mc=2.5, 5 MJup) | ~63 | not stated | au | 2 | sub-mm particles are trapped in the pressure peak at $\sim63$ au |
| Gas density peak, PDS 70b-only model | ~45 | not stated | au | 2 | PDS 70b opens a wide gap with the gas density peaking at about 45 au |
| Steady-state CPD dust mass (b, c) | 2.2e-5 and 4.5e-5 | not stated | Earth masses | 4 | This results in $M_{\rm dust, CPD}$ of $2.2\times10^{-5}~M_\ensuremath{\oplus}$ and $4.5\times10^{-5}~M_\ensuremath{\oplus}$. |
| Simulated CPD dust mass at 0.6 Myr (Mc=2.5) | (2-3)e-3 | not stated | Earth masses | 2 | the total dust mass in the CPDs at $t=0.6$ Myr reaches $(2-3) \times10^{-3}~M_\ensuremath{\oplus}$ |
| Resonance settling time | within 0.1 Myr | not stated | Myr | 2 | settle into 2:1 mean motion resonance within the first 0.1 Myr of the simulations for all three cases |

## Qualitative findings

- Two-planet models place the dust ring further out than the b-only model and match the observed ring; Mc=10 MJup gives ring eccentricity too large  
  > "we conclude that PDS 70c’s mass has to be smaller than 10 $M_{\rm Jup}$" (3.1 Disk Evolution)

## Claim tuples


## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: PDS 70b-only model rejected because the ring lies too close in (45 au vs ~74 au observed)  
  > "this is insufficient to explain the continuum peak at $\sim74$ au in the sub-mm observation" (3.1 Disk Evolution)
- How they decided it was enough: _not stated_
- Limitation (authors): Simulations do not address how the planets reached the resonant configuration  
  > "our simulations do not address how the two planets have reached such a configuration in the first place" (5 CONCLUSION)
- Caveat (inferred, ours): Fixed parameters (alpha, planet masses, dust size cut-off) not explored widely
- Caveat (inferred, ours): Agreement with observations is qualitative and not a quantitative fit
- Caveat (inferred, ours): 2D locally isothermal setup with no dust feedback

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Observed ALMA image and its reduction details
- Missing: Simulation parameter files
- Missing: Exact inclination and beam for the simulated observations
- Data volume (inferred): Not needed to reproduce simulations; ALMA continuum images are small (<10 GB)
- Score (inferred): 3/5, Simulation setup is well described and uses public codes, but the ALMA comparison details are missing.
- Rediscovery candidate: no, The paper is simulation-driven, the ALMA data are only used for a qualitative comparison, and the results are not mainly numeric.

## Links

- Method: (cite: baruteau19) (Dusty FARGO-ADSG code)
- Companion: (cite: keppler19) (ALMA observations of the PDS 70 disk)
- Companion: (cite: isella19) (ALMA detection of sub-mm emission near the planets)

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 23,
  "rate": 0.319
 },
 "evidence_ok": true
}
```
