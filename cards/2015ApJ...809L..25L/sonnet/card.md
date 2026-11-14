# The Distribution and Chemistry of H<SUB>2</SUB>CO in the DM Tau Protoplanetary Disk

`2015ApJ...809L..25L` | The Astrophysical Journal Letters 2015 | first author: Loomis, Ryan A. | arXiv: 1508.07004 | DOI: 10.1088/2041-8205/809/2/L25

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Do gas-phase and/or grain-surface reactions govern the H2CO distribution in the DM Tau disk?  
  > "to evaluate whether gas-phase chemistry significantly contributes to H$_2$CO abundances, or whether grain-surface chemistry truly dominates." (Introduction)
- Target **DM Tau**: coordinates RA 04h33m48.7s, Dec +18d10m09.8s (J2000, continuum peak)  
  > "continuum peak at $\alpha$J2000 = 04$^{h}$33$^{m}$48.7$^{s}$, $\delta$J2000 = 18$\degree$10$'$09.8$''$" (Results); "(94 x 65 AU at 145 pc)" (Observations); "inclination of 34$\degree$, and distance of 145 pc were assumed for the radiative transfer (cite: Teague_2015)" (Simulated observations of chemical models); z/distance 145 pc  
  > "continuum peak at $\alpha$J2000 = 04$^{h}$33$^{m}$48.7$^{s}$, $\delta$J2000 = 18$\degree$10$'$09.8$''$" (Results); "(94 x 65 AU at 145 pc)" (Observations); "inclination of 34$\degree$, and distance of 145 pc were assumed for the radiative transfer (cite: Teague_2015)" (Simulated observations of chemical models); distance from Teague et al. 2015  
  > "continuum peak at $\alpha$J2000 = 04$^{h}$33$^{m}$48.7$^{s}$, $\delta$J2000 = 18$\degree$10$'$09.8$''$" (Results); "(94 x 65 AU at 145 pc)" (Observations); "inclination of 34$\degree$, and distance of 145 pc were assumed for the radiative transfer (cite: Teague_2015)" (Simulated observations of chemical models)

## Data provenance

- ALMA projects: 2011.0.00629.S
- bands: Band 7  
  > "DM Tau was observed on 2012 October 23 in Band 7" (Observations)
- frequencies and spectral setup: four windows at 339.674, 340.366, 351.527, 354.264 GHz; 468.75 MHz each, 122.07 kHz (0.105 km/s) channels  
  > "The correlator spectral setup consisted of four windows centered at 339.674, 340.366, 351.527, and 354.264 GHz" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 17.5-380 m (20-430 klambda), 23 antennas  
  > "The array configuration included 23 antennas with projected baseline lengths between 17.5 and 380 m (20-430 k$\lambda$)" (Observations)
- angular resolution: 0.65" x 0.45" at PA ~-29 deg  
  > "providing a synthesized beam of 0.65" x 0.45" (94 x 65 AU at 145 pc) at a PA of $\sim$-29$\degree$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 35 minutes  
  > "The total integration time on-source was 35 minutes." (Observations)
- observing dates: 2012 October 23  
  > "DM Tau was observed on 2012 October 23" (Observations)
- pi or archival as stated: Archival; Cycle 0 project PI E. Chapillon  
  > "We use archival ALMA observations" (abstract)
- Line: H2CO 5_15-4_14 (351.769 GHz)
- External data: Physical disk model of DM Tau  
  > "We use the physical disk model of DM Tau derived in (cite: Andrews_2011)" (Chemical modeling) [from Andrews_2011]
- External data: Disk inclination 34 deg and position angle -24.3 deg, stellar mass 0.7 Msun  
  > "with an inclination of 34$\degree$ (cite: Teague_2015)" (Results) [from Teague_2015]
- External data: X-ray luminosity upper limit 4.6e29 erg/s  
  > "the X-ray upper limit is assumed from (cite: Damiani_1995) of $L_{\rm XR} \le 4.6\times10^{29}$ erg s$^{-1}$" (Chemical modeling) [from Damiani_1995]
- Simulation/model as data: Time-dependent disk chemistry models (gas-only, gas+grain, CH3OH as grain-only proxy), 1 Myr, ~6000 reactions, ~600 species  
  > "contains a total of $\sim6000$ reactions and $\sim600$ species" (Chemical modeling)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.2  
  > "We self-calibrated the data in CASA version 4.2 using the DM Tau disk continuum emission." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (flux), J0423-013 (bandpass), J0510+180 (phase)  
  > "Callisto was used for flux calibration, and J0423-013 was used as the bandpass calibrator." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: Self-calibrated on DM Tau disk continuum  
  > "We self-calibrated the data in CASA version 4.2 using the DM Tau disk continuum emission." (Observations)

### Imaging

- task: CASA clean, multi-frequency synthesis for continuum  
  > "We imaged the continuum emission using the multi-frequency synthesis mode of the CASA *CLEAN* task" (Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Initial mask from Keplerian disk model, then modified to fit emission  
  > "We generated an initial *CLEAN* mask using a simple model of a disk in Keplerian rotation and then modified it" (Observations)
- multiscale scales: _not stated_
- continuum subtraction: uv-plane continuum subtraction  
  > "we continuum subtracted the visibilities in the uv plane" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.5" x 1.0" restoring beam (217 x 145 AU)  
  > "applied a restoring beam of 1.5" x 1.0" (217 x 145 AU at 145 pc)" (Observations)
- final rms: ~0.16 mJy/beam continuum; ~10 mJy/beam per H2CO channel  
  > "The achieved rms is $\sim$0.16 mJy beam$^{-1}$ for the continuum and $\sim$10 mJy beam$^{-1}$ per H$_2$CO channel." (Observations)

### Inherited from earlier work

- Physical disk model of DM Tau  
  > "We use the physical disk model of DM Tau derived in (cite: Andrews_2011)" (Chemical modeling) [from Andrews_2011]
- Time-dependent chemical model; radiation field details  
  > "see (cite: Cleeves_2013; Cleeves_2014) for details" (Chemical modeling) [from Cleeves_2013; Cleeves_2014]

### Not stated but needed to reproduce (our reading)

- Robust/weighting, cell and image size, clean threshold
- Line-free channels for continuum and continuum subtraction
- Self-calibration solution intervals and number of rounds
- Deprojection radial bin widths and error estimation
- LIME settings (grid points, photons, collision rates)
- Abundance scaling factors applied to each model
- Chemical network files and model code availability

## Analysis recipe

1. **Image continuum and H2CO cube**: Self-calibrate, clean continuum, uv continuum-subtract, clean H2CO at 1.5"x1.0" beam with Keplerian-based mask  
  > "We generated an initial *CLEAN* mask using a simple model of a disk in Keplerian rotation and then modified it" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Moment-0 map and radial profiles**: immoments over 4-8 km/s; deproject with PA -24.3 deg and i=34 deg; azimuthal average about continuum peak  
  > "The moment map was created using the *immoments* command in CASA, summing over all channels observed to have H$_2$CO emission (4-8 km s$^{-1}$)." (Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Run disk chemistry models**: Three H2CO formation scenarios; 1 Myr; tests with reduced cosmic ray rate and 1% reactive desorption  
  > "we consider three different H$_2$CO formation scenarios: (1) gas-phase only; (2) both gas-phase and grain-surface; and (3) grain-surface reactions only." (Chemical modeling)
   - assumption: 10% reactive desorption, standard cosmic-ray rate, 1 Myr  
  > "we assume that $10\%$ of the time the grain-surface reactions result in desorption of the product" (Chemical modeling)
   - fitting: _not stated_
   - validation: Robustness tested with reduced cosmic ray ionization and reactive desorption  
  > "seem robust with respect to the assumed cosmic ray ionization rate and reactive desorption efficiency." (Chemical modeling)
4. **Simulate observations and compare profiles**: LIME non-LTE radiative transfer, simobserve with original array and integration time, scale abundances to match peak flux, compare radial profiles  
  > "the model abundances were uniformly scaled such that the peak integrated flux of the model and the observations match" (Simulated observations of chemical models)
   - software: LIME, CASA simobserve
   - assumption: M*=0.7 Msun, i=34 deg, d=145 pc  
  > "A stellar mass of 0.7 M$_{sun}$ (to determine line broadening), inclination of 34$\degree$, and distance of 145 pc were assumed" (Simulated observations of chemical models)
   - fitting: _not stated_
   - validation: Visual comparison of radial profiles  
  > "When comparing observed and simulated radial profiles, it is clear that the gas-phase model severely underpredicts emission in the outer disk." (Simulated observations of chemical models)

## Software

- **CASA** 4.2: Self-calibration, clean imaging, immoments, simobserve  
  > "We self-calibrated the data in CASA version 4.2" (Observations)
- **LIME** : Non-LTE radiative transfer of H2CO 5_15-4_14  
  > "using the non-LTE radiative transfer code LIME (cite: Brinch_2010)" (Simulated observations of chemical models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H2CO emission half-light radius | ~270 | not stated | not stated (AU presumably) | 2 | with a half-light radius of $\sim$270. |
| Model overprediction of line fluxes | 2-10 | not stated | dimensionless | 4 | The original model output overpredicted the line fluxes by factors of 2–10. |
| CO snowline radius in model | ~80 | not stated | AU | 3 | outside the CO snowline at $\sim$80 AU there is a rise in column density |

## Qualitative findings

- H2CO emission is centrally peaked and radially broad, with no ring or hole  
  > "displaying a large H$_2$CO emission disk without any apparent hole or gap" (Results)

## Claim tuples

- H: Both gas-phase and grain-surface chemistry contribute to disk H2CO | E: Compare observed radial profile with gas-only, gas+grain and grain-only chemical models | R: Gas-only underpredicts outer emission; grain-only overpredicts beyond 100 AU; gas+grain is closest | F: Both pathways are needed; gas-phase gives the central peak, grain-surface the emission beyond the CO snowline | **supported**
- H: The ring reported by Henning & Semenov 2008 is real | E: Compare ALMA 5_15-4_14 with earlier 3_13-2_12 PdBI data and LIME simulation | R: ALMA shows centrally peaked emission | F: The earlier ring may be partly due to excitation and sensitivity | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Spatial distribution should discriminate between formation pathways  
  > "The spatial distribution of H$_2$CO should contain information on the contributions of these formation mechanisms." (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Model overpredicts fluxes; abundances rescaled; grain-only case proxied by CH3OH since H2CO gas-phase cannot be switched off  
  > "It is not possible to turn off H$_2$CO gas-phase formation and destruction pathways in the model while leaving reactions on the grains" (Chemical modeling)
- Caveat (inferred, ours): Qualitative by-eye model comparison, no quantitative fit or uncertainties
- Caveat (inferred, ours): Single transition, so excitation and vertical structure are degenerate
- Caveat (inferred, ours): Coarse 1.5" beam, few models
- Caveat (inferred, ours): No error bars on radial profile

## Reproducibility

- Data public (paper): Archival Cycle 0 data  
  > "We use archival ALMA observations" (abstract)
- Products in archive: _not stated_
- Missing: Chemical model code and exact setups
- Missing: LIME parameters
- Missing: Clean parameters and self-cal details
- Data volume (inferred): ~5-20 GB
- Score (inferred): 3/5, Public data and a clear outline, but the chemical modeling is not reproducible from the text and imaging parameters are missing.
- Rediscovery candidate: no, Main conclusions are qualitative and depend on a non-public chemical code.

## Links

- Method: Cleeves_2014 (Time-dependent chemical model)
- Method: Brinch_2010 (LIME radiative transfer code)
- Companion: Henning_2008 (Earlier PdBI H2CO observations of DM Tau)
- Companion: Qi_2013_H2CO (H2CO in HD 163296)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
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
  "facts": 67,
  "stated": 39,
  "rate": 0.582
 },
 "evidence_ok": true
}
```
