# An ALMA Dynamical Mass Estimate of the Proposed Planetary-mass Companion FW Tau C

`2017ApJ...846L..26W` | The Astrophysical Journal Letters 2017 | first author: Wu, Ya-Lin | arXiv: 1708.08122 | DOI: 10.3847/2041-8213/aa8771

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Is FW Tau C a ~10 Mjup planetary-mass companion or a low-mass star? Measured via Keplerian rotation of its resolved CO (2-1) disk.  
  > "Accurate mass measurement is therefore key to distinguishing the planet-mass scenario from the stellar-mass scenario." (1. Introduction)
- Target **FW Tau C (companion to FW Tau AB)**: coordinates _not stated_; z/distance ~140 pc  
  > "Distance (pc)                 | $\sim$140" (Table 1); "FW Tau C is a tertiary companion located at $\sim$2.3$''$ projected separation ($\sim$330 au) to FW Tau AB" (1. Introduction); distance from Kenyon et al. 1994 (cite: K94)  
  > "Distance (pc)                 | $\sim$140" (Table 1); "FW Tau C is a tertiary companion located at $\sim$2.3$''$ projected separation ($\sim$330 au) to FW Tau AB" (1. Introduction)

## Data provenance

- ALMA projects: 2015.1.00773.S
- bands: Band 6 (1.3 mm), Cycle 3  
  > "FW Tau was observed with ALMA Band 6 during Cycle 3, on 2016 September 14." (2.1 Observations and Data Reduction)
- frequencies and spectral setup: Continuum basebands at 233.0, 246.0, 248.0 GHz; CO baseband with 3840 0.122 MHz channels centered at 230.538 GHz (0.32 km/s, Hanning smoothed)  
  > "The last baseband was configured with 3840 0.122 MHz channels centered at 230.538 GHz (0.32 km s$^{-1}$ velocity resolution; Hanning smoothed)" (2.1 Observations and Data Reduction)
- continuum bandwidth: 2 GHz per baseband  
  > "centered at 233.0, 246.0, and 248.0 GHz and each with 2 GHz of bandwidth" (2.1 Observations and Data Reduction)
- arrays: thirty-six 12 m antennas  
  > "During the observations thirty-six 12 m antennas were available, with baselines ranging from 15 to 3247 m." (2.1 Observations and Data Reduction)
- configurations: _not stated_
- baselines: 15 to 3247 m  
  > "with baselines ranging from 15 to 3247 m" (2.1 Observations and Data Reduction)
- angular resolution: ~0.2'' beam  
  > "With a $\sim$0.2$''$ beam and $\sim$0.3 km s$^{-1}$ velocity resolution" (1. Introduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~13 minutes  
  > "The on-source time was $\sim$13 minutes." (2.1 Observations and Data Reduction)
- observing dates: 2016 September 14  
  > "on 2016 September 14" (2.1 Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- External data: Distance ~140 pc  
  > "Distance (pc)                 | $\sim$140" (Table 1) [from (cite: K94)]
- External data: Previous planetary mass 10±4 Mjup from dereddened K' flux  
  > "(cite: K14) derived a planetary mass of $10\pm4$ $M_{\rm Jup}$ from its dereddened $K'$ flux" (1. Introduction) [from (cite: K14)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA  
  > "The data were reduced using the ALMA pipeline in the `CASA` package." (2.1 Observations and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800 (bandpass and flux); J0433+2905 gain  
  > "J0510+1800 was used as the bandpass and flux calibrator, and J0433+2905 was used as the the gain calibrator." (2.1 Observations and Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: One iteration of phase-only self-cal on 2 GHz continuum basebands; not possible for CO baseband  
  > "We employed one iteration of phase-only self-calibration to the 2 GHz continuum basebands." (2.1 Observations and Data Reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting, multi-frequency synthesis  
  > "We then CLEANed the calibrated data using the multi-frequency synthesis mode and natural weighting to enhance sensitivity in the images." (2.1 Observations and Data Reduction)
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
- final beam: continuum 0.29''x0.15'' PA 160.8°; CO 0.30''x0.16'' PA 160.3°  
  > "The CO channel maps (top panel of Figure [3](#fig:channel_maps)) have a beam size of $0.30\ensuremath{''}\times0.16\ensuremath{''}$ with a PA of $160.3\ensuremath{^\circ}$" (2.1 Observations and Data Reduction)
- final rms: continuum 35 uJy/beam; CO 4.5 mJy/beam in signal-free channels  
  > "a mean rms of 4.5 mJy beam$^{-1}$ in signal-free channels" (2.1 Observations and Data Reduction)

### Inherited from earlier work

- Keplerian disk modeling procedure (radiative transfer channel-map fitting) follows earlier work, with own codes  
  > "we follow the modeling procedure described in (cite: Cz15) to fit our channel maps with synthetic channel maps produced from radiative transfer models." (2.3 Disk Modeling: Keplerian Rotation) [from (cite: Cz15)]
- Distance uncertainty of 20 pc  
  > "Here, we assume a conservative distance uncertainty of 20 pc following (cite: Cz16)." (2.3 Disk Modeling: Keplerian Rotation) [from (cite: Cz16)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- CLEAN threshold, cell and image size, masks
- MCMC walker number, steps, burn-in, prior ranges
- Self-calibration solution interval
- Disk-mass uncertainty treatment; custom code not released
- Moment-map clipping and PV extraction details
- Continuum subtraction method for CO

## Analysis recipe

1. **Calibrate and image data**: ALMA pipeline in CASA, phase-only self-cal on continuum, CLEAN with MFS and natural weighting  
  > "We then CLEANed the calibrated data using the multi-frequency synthesis mode and natural weighting to enhance sensitivity in the images." (2.1 Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit continuum geometry and dust mass**: Uniform-brightness inclined disk fit to continuum visibilities with MCMC; dust mass from optically thin formula  
  > "We fit the model directly to the continuum visibilities using the Markov Chain Monte Carlo (MCMC) package `emcee`" (2.2 Disk Modeling: Continuum)
   - software: emcee
   - assumption: T = 20 K, kappa = 2.3 cm^2/g, distance 140 pc, optically thin  
  > "We use standard assumptions of $T = 20$ K and $\kappa_{\nu} = 2.3$ cm$^2$ g$^{-1}$ and a distance to FW Tau C of 140 pc." (2.2 Disk Modeling: Continuum)
   - fitting: emcee MCMC on visibilities  
  > "We fit the model directly to the continuum visibilities using the Markov Chain Monte Carlo (MCMC) package `emcee`" (2.2 Disk Modeling: Continuum)
   - validation: _not stated_
3. **Fit Keplerian CO disk model for stellar mass**: RADMC-3D synthetic 12CO(2-1) channel maps, Fourier transformed and fit to visibilities with emcee  
  > "Those synthetic channel maps are Fourier transformed and fit directly to the visibilities using the MCMC fitting package `emcee` (cite: FM13), with uniform priors for all parameters." (2.3 Disk Modeling: Keplerian Rotation)
   - software: RADMC-3D, emcee
   - parameter: Free: Mdisk, Rdisk, gamma, T0, q, xi, M*, vsys, inclination, PA, small centering offset  
  > "the density, temperature, and velocity structure of the system are described by the following parameters: $M_{\rm disk}$, $R_{\rm disk}$, $\gamma$, $T_0$, $q$, $\xi$, $M_*$, and $v_{\rm sys}$." (2.3 Disk Modeling: Keplerian Rotation)
   - assumption: Flared LTE vertically isothermal Keplerian disk; X_CO=1e-4; mu=2.37; inner radius 0.1 au; distance 140 pc with 20 pc uncertainty added in quadrature  
  > "Here, $X_{\rm CO} = 1 \times 10^{-4}$ is the CO mass abundance fraction, and $\mu = 2.37$ is the mean molecular weight." (2.3 Disk Modeling: Keplerian Rotation)
   - fitting: emcee, uniform priors, 128 CPUs, few days  
  > "we run the fit over 128 CPUs on the University of Arizona El Gato supercomputer, and the modeling took a few days to converge." (2.3 Disk Modeling: Keplerian Rotation)
   - validation: Convergence when walkers reached steady state; PV diagram compared with 10 Mjup and 0.1 Msun Keplerian curves  
  > "The models were determined to be converged when the `emcee` walkers had reached a steady state with measured best-fit values changing minimally over a large number of steps." (2.3 Disk Modeling: Keplerian Rotation)

## Software

- **CASA** : ALMA pipeline reduction, self-calibration, CLEAN imaging  
  > "The data were reduced using the ALMA pipeline in the `CASA` package." (2.1 Observations and Data Reduction)
- **emcee** : MCMC fitting of continuum and CO visibilities  
  > "Markov Chain Monte Carlo (MCMC) package `emcee` (cite: FM13)" (2.2 Disk Modeling: Continuum)
- **RADMC-3D** : Synthetic 12CO(2-1) channel maps from disk models  
  > "We use the 3D radiative transfer modeling package `RADMC-3D` (cite: Dullemond12) to calculate the level populations in each cell" (2.3 Disk Modeling: Keplerian Rotation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stellar (dynamical) mass of FW Tau C | 0.098 | 0.015 | Msun | 3 | $M_*$ ($M_\odot$)                                / $0.098 \pm 0.015$ |
| Dust mass | 1.15 | 0.01 | Mearth | 2 | $1.15 \pm 0.01$ |
| Gas disk radius | 141.9 | 6.6 | au | 3 | $141.9 \pm 6.6$ |
| Inclination | 62.8 | 2.4 | deg | 3 | $62.8 \pm 2.4$ |
| Position angle | 40.6 | 1.5 | deg | 3 | $40.6 \pm 1.5$ |
| Systemic velocity | 6.10 | 0.02 | km/s | 3 | $6.10 \pm 0.02$ |
| Gas mass | 0.58 | 0.13 | Mearth | 3 | $0.58\pm0.13$ |
| 1.3 mm continuum flux | ~2.06 | not stated | mJy | 2 | it has a 1.3 mm flux of $\sim$2.06 mJy |
| FW Tau AB dust mass 3sigma upper limit | <~0.07 | not stated | Mearth | 2 | the $3\sigma$ upper limit for a unresolved source suggests a dust mass $\lesssim$0.07 $M_\oplus$ |

## Qualitative findings

- FW Tau C gas disk is resolved and Keplerian; FW Tau AB undetected  
  > "its dust disk is compact and likely unresolved; in contrast, the gas disk is more extended and clearly shows a Keplerian rotation." (3. Results)

## Claim tuples

- H: FW Tau C is a ~10 Mjup planet | E: Keplerian modeling of resolved 12CO(2-1) disk and PV diagram | R: M* = 0.098±0.015 Msun; velocity profile incompatible with 10 Mjup | F: FW Tau C is a low-mass star with an inclined disk; FW Tau is a triple of ~0.1 Msun stars | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: 10 Mjup planetary-mass scenario rejected in favor of low-mass star embedded in an inclined disk  
  > "Hence, FW Tau C is not a planetary-mass object, but is rather a low-mass star with an inclined disk" (3. Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Single optically thick CO line likely underestimates gas mass  
  > "with a single optically thick CO line, we are very likely to underestimate the true gas mass by a factor of few or even orders of magnitude" (3. Results)
- Caveat (inferred, ours): Mass depends linearly on assumed 140 pc distance
- Caveat (inferred, ours): Low S/N CO; inclination allowed 0-90 deg
- Caveat (inferred, ours): No fit-quality or convergence statistics given
- Caveat (inferred, ours): Custom code not released

## Reproducibility

- Data public (paper): Project code given in acknowledgments  
  > "This Letter makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00773.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Custom fitting code not provided
- Missing: MCMC settings and priors ranges
- Missing: CASA version and clean parameters
- Data volume (inferred): ~10-20 GB
- Score (inferred): 3/5, Short observation, public data, clear model description, but custom code and MCMC and imaging details are missing.
- Rediscovery candidate: no, The model fit relies on unreleased custom code and unstated settings, although the data are public.

## Links

- Method: Czekala et al. 2015 (cite: Cz15) (Disk modeling procedure followed)
- Companion: Kraus et al. 2015 (cite: K15) (Earlier ALMA continuum detection)
- Companion: Caceres et al. 2015 (cite: C15) (Earlier ALMA CO detection)
- Companion: Bowler et al. 2014 (cite: B14) (Suggested low-mass star in edge-on disk)

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 37,
  "rate": 0.561
 },
 "evidence_ok": true
}
```
