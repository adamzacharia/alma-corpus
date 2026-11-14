# GW Ori: Interactions between a Triple-star System and Its Circumtriple Disk in Action

`2020ApJ...895L..18B` | The Astrophysical Journal Letters 2020 | first author: Bi, Jiaqing | arXiv: 2004.03135 | DOI: 10.3847/2041-8213/ab8eb4

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What substructures (rings, eccentricity, misalignment) does the circumtriple disk of GW Ori have, and do they indicate ongoing interactions with the triple stars?  
  > "where we find new substructures of the disk that indicate ongoing disk-star interactions." (Introduction)
- Target **GW Ori**: coordinates _not stated_; z/distance 402 ± 10 pc  
  > "GW Ori is a hierarchical triple system (cite: berger2011) at a distance of 402 $\pm$ 10 parsec (cite: gaia2018)." (Introduction); distance from Gaia DR2 (gaia2018)  
  > "GW Ori is a hierarchical triple system (cite: berger2011) at a distance of 402 $\pm$ 10 parsec (cite: gaia2018)." (Introduction)

## Data provenance

- ALMA projects: 2017.1.00286.S
- bands: Band 6 (1.3 mm)  
  > "The disk was observed in Band 6 (1.3 mm) by 46 antennas, with baseline lengths ranging from 15 to 3321 meters." (Observation and Data Reduction)
- frequencies and spectral setup: Continuum basebands 1.875 GHz wide at 217 and 233 GHz; three line basebands of 117 MHz, 112 kHz resolution at 230.518, 219.541, 220.380 GHz  
  > "There were two 1.875-GHz-wide basebands centered at 217 and 233 GHz for continuum emission, and three basebands with 117 MHz bandwidths and 112 kHz resolution" (Observation and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 to 3321 m, 46 antennas  
  > "The disk was observed in Band 6 (1.3 mm) by 46 antennas, with baseline lengths ranging from 15 to 3321 meters." (Observation and Data Reduction)
- angular resolution: 0.098" (~39 AU) continuum  
  > "Figure [\[fig:obs\]](#fig:obs)a shows the continuum map with spatial resolution of 0".098 ($\sim$ 39 AU)." (3.1 Dust Continuum Emission)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 1.6 hours  
  > "The total on source integration time was 1.6 hours." (Observation and Data Reduction)
- observing dates: December 10, 2017  
  > "The observations were taken on December 10, 2017 (ID: 2017.1.00286.S)." (Observation and Data Reduction)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.518 GHz)
- External data: Stellar masses ~2.7, 1.7, 0.9 Msun and AB-C orbit inclination/node  
  > "The stellar masses have been constrained to be $\sim$ 2.7, 1.7, and 0.9 $M_\odot$, respectively (cite: czekala2017)." (Introduction) [from (cite: czekala2017)]
- External data: Stellar luminosity 49.3 ± 7.4 Lsun (Gaia-corrected)  
  > "The stellar luminosity modified by the distance provided by GAIA DR2 is 49.3 $\pm$ 7.4 $L_{\odot}$ (cite: calvet2004; gaia2018)." (3.1 Dust Continuum Emission) [from (cite: calvet2004; gaia2018)]
- External data: Dust opacity 10 cm2/g at 1000 GHz, index 1  
  > "We assume a dust grain opacity of 10 cm^2^ g^-1^ at 1000 GHz with a power-law index of 1 (cite: beckwith1990)." (3.1 Dust Continuum Emission) [from (cite: beckwith1990)]
- Simulation/model as data: DALI 12CO channel-map models of a misaligned disk, and a PHANTOM SPH simulation of the disk around the binary  
  > "The ^12^CO channel maps are then computed and ray-traced by the physical-chemical modeling code DALI (cite: bruderer2013)" (4.2 Kinematics Modelling)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline calibration script  
  > "The data were calibrated by the pipeline calibration script provided by ALMA." (Observation and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Phase self-calibration, solint 20 s  
  > "We performed phase self-calibration onto the image with a solution interval of 20 seconds." (Observation and Data Reduction)

### Imaging

- task: CASA CLEAN  
  > "We adopted CASA task CLEAN to image the continuum map" (Observation and Data Reduction)
- deconvolver: _not stated_
- weighting robust: Continuum: uniform; CO: Briggs robust = 0.5  
  > "in the BRIGGS weighting scheme with robust = 0.5, and velocity resolution 0.5 km s^-1^." (Observation and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum subtracted from self-calibrated data  
  > "(after subtracting the continuum on the self-calibrated data)" (Observation and Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: continuum 0.098" circular; CO 0.122" x 0.159", PA -32.3 deg  
  > "The resulting line cube has a beam size of 0".122 $\times$ 0".159 at the position angle -32.3^$\circ$^." (Observation and Data Reduction)
- final rms: continuum ~40 uJy/beam; CO ~1.4 mJy/beam per channel  
  > "The noise level is $\sim$ 1.4 mJy beam^-1^ per channel and the peak signal-to-noise ratio is $\sim$ 83." (Observation and Data Reduction)

### Inherited from earlier work

- Gas surface density and aspect-ratio prescription and parameters for CO modelling  
  > "Following the prescription and parameter values used to fit low resolution CO isotopologue data of GW Ori (cite: fang2017)" (4.2 Kinematics Modelling) [from (cite: fang2017)]
- Misaligned-annuli gas modelling approach  
  > "Similar to (cite: walsh2017), we model the misaligned disk with an inner cavity and three annuli" (4.2 Kinematics Modelling) [from (cite: walsh2017)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- CLEAN threshold, mask, cell and image size, number of iterations
- Self-calibration reference model and how many rounds
- MCMC priors' numeric bounds, initial walker positions, and convergence checks
- Line-free channels and moment-map details
- DALI chemistry and model setup details beyond Table 4
- Flux scale calibrator

## Analysis recipe

1. **Image continuum and CO**: Pipeline calibration, phase self-cal, CASA CLEAN with uniform weighting (continuum) and Briggs robust 0.5 (CO)  
  > "We adopted CASA task CLEAN to image the continuum map (Figure [\[fig:obs\]](#fig:obs)a), with the UNIFORM weighting scheme and a 0".098 circular restoring beam." (Observation and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: Flux consistent with previous ALMA observations  
  > "The integrated flux density of the disk (195 $\pm$ 20 mJy) is consistent with the result from previous ALMA observations (cite: czekala2017)." (Observation and Data Reduction)
2. **Estimate ring dust masses**: Optically thin dust mass equation with ring-radius dependent dust temperature  
  > "We estimate the dust (solid) mass $M_{\text{dust}}$ of the rings with the equation provided in (cite: hildebrand1983)" (3.1 Dust Continuum Emission)
   - assumption: T_dust = 30 (L/38 Lsun)^1/4 (r/100 AU)^-1/2; kappa 10 cm2/g at 1000 GHz, index 1; d=402 pc  
  > "We assume a dust grain opacity of 10 cm^2^ g^-1^ at 1000 GHz with a power-law index of 1 (cite: beckwith1990)." (3.1 Dust Continuum Emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Visibility modelling of dust rings**: Three Gaussian-profile rings fitted in visibilities; Model 1 independent inclined circular rings; Models 2/3 eccentric inner ring  
  > "We fit the dust continuum map assuming that there are three dust rings in the disk with Gaussian radial profiles of surface brightness" (4.1 Visibility Modelling)
   - software: GALARIO, emcee
   - parameter: 144 chains, 15000 iterations including 10000 burn-in  
  > "For each model, there are 144 chains spread in the hyperspace of parameters. Each chain has 15000 iterations including 10000 burn-in iterations." (4.1 Visibility Modelling)
   - fitting: emcee MCMC, Gaussian likelihood on real and imaginary visibilities with weights; flat bounds priors  
  > "The prior function is set to guarantee the surface brightness, ring radius, and ring width do not go below zero" (4.1 Visibility Modelling)
   - validation: Residual map from visibility subtraction; uv-plot and posteriors shown  
  > "The residual map is produced by subtracting model from data in the visibility plane, and then imaging the results in the same way used for the observations." (4.1 Visibility Modelling)
4. **CO kinematics modelling**: DALI models with three annuli of different inclination/PA, run through ALMA simulator, compared with first-moment map against coplanar model by eye  
  > "The channel map is run through the ALMA simulator using the settings of the ALMA observations." (4.2 Kinematics Modelling)
   - software: DALI
   - parameter: disk mass 0.12 Msun, Sigma_c=3 g/cm2, rc=320 AU, gamma=1.0, (h/r)c=0.18, psi=0.1, gas-to-dust 100  
  > "with $\gamma$ = 1.0, $(h/r)_c$ = 0.18 and $\psi$ = 0.1." (4.2 Kinematics Modelling)
   - fitting: Manual fitting  
  > "the manual fitting of gas model cannot provide any uncertainties for the gap between the inner and middle ring" (Footnote 2)
   - validation: Compared with coplanar model  
  > "The models show that the ^12^CO $J=2-1$ first-moment map in the ALMA observation cannot be reproduced by a coplanar disk." (4.2 Kinematics Modelling)
5. **Timescale analysis and SPH simulation**: Analytic radial communication, precession and alignment timescales; PHANTOM SPH simulation with 10^6 particles  
  > "We carry out a demonstrative smoothed particle hydrodynamic (SPH) simulation with the PHANTOM code" (5.4 Hydrodynamic Simulations)
   - software: PHANTOM
   - parameter: alpha_AV=0.31, h/r=0.05, disk mass 0.1 Msun, 40-400 AU  
  > "We take a locally isothermal disk with a constant aspect ratio $h/r=0.05$" (5.4 Hydrodynamic Simulations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data processing and imaging  
  > "We used the Common Astronomy Software Applications package (cite: mcmullin2007) to process the data." (Observation and Data Reduction)
- **GALARIO** : Synthetic visibilities  
  > "we calculate the synthetic visibility of the models using GALARIO (cite: tazzari2018)" (4.1 Visibility Modelling)
- **emcee** : MCMC parameter surveys  
  > "launch MCMC parameter surveys to derive posterior distribution of model parameters using EMCEE (cite: dfm2013)" (4.1 Visibility Modelling)
- **DALI** : Ray-traced 12CO channel maps  
  > "ray-traced by the physical-chemical modeling code DALI (cite: bruderer2013)" (4.2 Kinematics Modelling)
- **PHANTOM** : SPH simulation of disk  
  > "with the PHANTOM code (cite: lodato2010; price2010; price2018)" (5.4 Hydrodynamic Simulations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Ring radii | 46, 188, 338 | not stated | AU | 3 | We identify three dust rings with different apparent shapes in the disk at $\sim$ 46, 188, and 338 AU |
| Dust masses (inner, middle, outer) | 74, 168, 245 | ±8, ±19, ±28 | Earth masses | 2 | We estimate the dust masses of the rings to be 74 $\pm$ 8, 168 $\pm$ 19, and 245 $\pm$ 28 $M_\oplus$, respectively |
| Ring flux densities (inner, middle, outer) | 42, 95, 58 | ±4, ±10, ±6 | mJy | 1 | The continuum flux densities of the inner, middle, and outer ring are 42 $\pm$ 4, 95 $\pm$ 10 and 58 $\pm$ 6 mJy, respectively. |
| Total continuum flux density | 195 | 20 | mJy | 1 | The integrated flux density of the disk (195 $\pm$ 20 mJy) |
| Inner ring eccentricity (Model 3) | 0.19 | +8.55e-4/-6.46e-4 | dimensionless | 3 | Eccentricity / $0.19\;^{+8.55\times10^{-4}}_{-6.46\times10^{-4}}$ |
| Binary-disk misalignment (46, 188, 338 AU) | 11, 35, 40 | ±6, ±5, ±5 | degrees | 3 | are 11 $\pm$ 6, $\sim$28[^2], 35 $\pm$ 5, and 40 $\pm$ 5 degrees, respectively. |
| Global precession and radial communication timescales | 0.83 and 0.06 | not stated | Myr | 5 | the global precession time-scale of the entire disk is $\sim$ 0.83 Myr, and the radial communication time-scale is $\sim$ 0.06 Myr |

## Qualitative findings

- Outermost ring is the largest dust ring found in a protoplanetary disk; CO first-moment map shows a twisted pattern inside ~0.2" suggesting misalignment.  
  > "we find a twisted pattern inside $\sim$ 0".2, which may result from a misalignment between the inner and outer parts of the disk" (Observational Results, ^12^CO J=2-1 Emission)

## Claim tuples

- H: Disk rings are misaligned/eccentric | E: MCMC visibility modelling with three models | R: Different centers and inclinations; inner ring e~0.19-0.21 | F: Inner ring is eccentric and rings are mutually misaligned | **supported**
- H: CO kinematics indicate misalignment | E: DALI misaligned vs coplanar first-moment maps | R: Coplanar model fails | F: Disk is warped/misaligned | **supported**
- H: Triple star torque alone explains inner/middle misalignment | E: Analytic timescales and SPH simulation | R: Disk does not break | F: Another mechanism (e.g. companion) needed to break the disk | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Coplanar disk (i=37.9, PA=-5) rejected for CO kinematics; viscous-regime breaking disfavoured by low observed alpha  
  > "in which the disk is coplanar with an inclination of 37.9^$\circ$^ and a position angle of -5^$\circ$^." (4.2 Kinematics Modelling)
- How they decided it was enough: _not stated_
- Limitation (authors): Mutual inclinations cannot be determined from dust alone due to unknown orbital direction; gas model has no uncertainties for the gap.  
  > "we cannot determine the mutual inclinations between them (i.e., the angles between their angular momentum vectors) from dust emission modelling alone" (4.1 Visibility Modelling)
- Caveat (inferred, ours): Dust masses depend on assumed opacity and temperature law and optically thin assumption
- Caveat (inferred, ours): Gas model fit is manual with no quantitative goodness of fit
- Caveat (inferred, ours): Gaussian ring models leave residuals

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA/pipeline versions
- Missing: CLEAN parameters
- Missing: MCMC priors/initialization
- Missing: DALI full setup
- Data volume (inferred): ~100-300 GB raw for one long-baseline Band 6 execution
- Score (inferred): 3/5, Single public dataset and a clear model structure, but imaging parameters and fitting details are incomplete.
- Rediscovery candidate: yes, Public data, numeric ring radii, masses and ring-fit parameters can be reproduced with moderate assumptions.

## Links

- Method: (cite: tazzari2018) (GALARIO visibility modelling)
- Method: (cite: bruderer2013) (DALI code)
- Companion: (cite: czekala2017) (Previous ALMA observations and orbit)
- Companion: (cite: fang2017) (Low-resolution CO modelling and disk structure)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
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
  "facts": 76,
  "stated": 44,
  "rate": 0.579
 },
 "evidence_ok": true
}
```
