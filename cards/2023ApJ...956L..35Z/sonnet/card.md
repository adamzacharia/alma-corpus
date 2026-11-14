# One, Two, Three ... An Explosive Outflow in IRAS 12326-6245 Revealed by ALMA

`2023ApJ...956L..35Z` | The Astrophysical Journal Letters 2023 | first author: Zapata, Luis A. | arXiv: 2309.11386 | DOI: 10.3847/2041-8213/acfe71

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation
- Question: Does the massive star-forming region IRAS 12326-6245 host an explosive outflow (streamers with Hubble-Lemaitre-like expansion), and what are its age, energy and the implied Galactic event rate?  
  > "Here, we report one more explosive outflow related with the massive and bright star-forming region IRAS 12326$-$6245 using Band 6 sensitive and high angular resolution ($\sim$0.2$''$) Atacama Large Millimeter/Submillimeter Array (ALMA) observations." (abstract)
- Target **IRAS 12326-6245 (G301.1364-00.2249)**: coordinates RA 12h35m35.13s, Dec -63d02'30.8" (J2000, phase center)  
  > "In this work, we adopt the 2.03 kpc distance derived by (cite: 2021Duronea)." (Introduction); "The observations were pointed at the phase center located in the sky position $\alpha_{J2000.0}$ = $12^{\rm h}35^{\rm m}35\mbox{$^{\rm s}\mskip-7.6mu.\,$}13$" (2 Observations); z/distance 2.03 kpc  
  > "In this work, we adopt the 2.03 kpc distance derived by (cite: 2021Duronea)." (Introduction); "The observations were pointed at the phase center located in the sky position $\alpha_{J2000.0}$ = $12^{\rm h}35^{\rm m}35\mbox{$^{\rm s}\mskip-7.6mu.\,$}13$" (2 Observations); distance from Duronea et al. 2021  
  > "In this work, we adopt the 2.03 kpc distance derived by (cite: 2021Duronea)." (Introduction); "The observations were pointed at the phase center located in the sky position $\alpha_{J2000.0}$ = $12^{\rm h}35^{\rm m}35\mbox{$^{\rm s}\mskip-7.6mu.\,$}13$" (2 Observations)

## Data provenance

- ALMA projects: 2016.1.01347.S
- bands: Band 6 (1.3 mm)  
  > "using Band 6 sensitive and high angular resolution ($\sim$0.2$''$)" (abstract)
- frequencies and spectral setup: 8 SPWs; SPW1 centered at 230.551 GHz, 1920 channels, 317 m/s spacing  
  > "we concentrate on the SPW1 centered at 230.551 GHz, with a 244.141 kHz width, and divided into 1920 spectral channels, which resulted in a channel spacing of 317 m s$^{-1}$" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m antennas only  
  > "This science data program only included 12 m diameter antennas with projected baselines ranging from 16.7 to 3700 m" (2 Observations)
- configurations: _not stated_
- baselines: 16.7 to 3700 m  
  > "projected baselines ranging from 16.7 to 3700 m (12.8 to 2846 k$\lambda$)" (2 Observations)
- angular resolution: 0.21x0.18" continuum; 0.18x0.15" line  
  > "at an angular resolution of 0.21$''$ $\times$ 0.18$''$ with a Position Angle (PA) of $-$68.2$^\circ$" (2 Observations)
- max recoverable scale: 5.6"  
  > "The largest angular scale that can be recovered with the present observations is 5.6$''$." (2 Observations)
- sensitivity: _not stated_
- time on source: 66 min in 7-pointing mosaic  
  > "The total integrated time on source was 66 min, distributed in the 7-pointing mosaic." (2 Observations)
- observing dates: 2017 July 20 and 23  
  > "in 2017 July 20 (with 41 antennas) and 23 (with 44 antennas)" (2 Observations)
- pi or archival as stated: Archival data, PI Silvia Leurini  
  > "(PI: Silvia Leurini)" (2 Observations)
- Line: 12CO J=2-1 (230.5379700 GHz)
- External data: Distance 2.03 kpc to S169 and IRAS 12326-6245  
  > "estimated a new distance to both structures of 2.03$^{+0.77}_{-0.61}$ kpc" (Introduction) [from (cite: 2021Duronea)]
- External data: Cloud LSR systemic velocity -39.5 km/s  
  > "which is $-$39.5 km s$^{-1}$ (cite: 2021Duronea)" (3 Results) [from (cite: 2021Duronea)]
- External data: Dust grain opacity 0.897 cm2/g (beta=1.1)  
  > "a grain opacity of 0.897 cm$^2$g$^{-1}$ (using the measured dust emissivity spectral index $\beta=1.1$)" (3 Results) [from (cite: 1994Ossen)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 6.4.1.12  
  > "Common Astronomy Software Applications (CASA) package, Version 6.4.1.12" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Quasars J1107-4449, J1252-6737, J1206-6138 (bandpass, gain, flux)  
  > "Quasars J1107$-$4449, J1252$-$6737, and J1206$-$6138 were used to calibrate the bandpass, the atmosphere and the gain fluctuations, and the flux amplitude." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: Phase self-calibration using continuum as model, applied to line channels; rms improved ~3x  
  > "Using the continuum as a model, we undertook phase self-calibration, we then applied the acquired solutions to the spectral line channels." (2 Observations)

### Imaging

- task: TCLEAN  
  > "The data was imaged using the routine `TCLEAN`" (2 Observations)
- deconvolver: _not stated_
- weighting robust: robust 2.0 for continuum; 0.5 for lines  
  > "We used a robust equals to 2.0 in `TCLEAN`." (2 Observations); "We used a robust equals to 0.5 in `TCLEAN`." (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Continuum from line-free channels of the eight SPWs (channels not listed)  
  > "We used the eight spectral windows to average line-free channels in order to obtain the continuum image." (2 Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: continuum 0.84 mJy/beam; line 2.1 mJy/beam km/s  
  > "rms-noise for the continuum at 1.3 mm of 0.84 mJy beam$^{-1}$" (2 Observations)

### Inherited from earlier work

- Dust shell mass assumptions (optically thin, gas-to-dust 100, T 75-150 K)  
  > "adopting the same assumptions as for the mass estimate of the dust shell in G5.89$-$0.39 (cite: 2021Manuel)" (3 Results) [from (cite: 2021Manuel)]
- Streamer tracing via CO condensations in cube channels  
  > "this procedure has been used already in many other studies, see for example (cite: 2009Zapata; 2013Zapata; 2020Zapata; 2022GuzmanCcolque)" (3 Results) [from (cite: 2009Zapata; 2013Zapata; 2020Zapata; 2022GuzmanCcolque)]
- CO outflow mass from LTE equation 2  
  > "following the equation 2 presented in (cite: 2020Cortes)" (3 Results) [from (cite: 2020Cortes)]
- Galactic event rate method  
  > "Following (cite: 2020Zapata; 2022GuzmanCcolque), we can update the rate of explosive outflows in the Galaxy." (4 Discussion) [from (cite: 2020Zapata; 2022GuzmanCcolque)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum
- Cleaning threshold, masks, niter, image size and cell size
- How streamer condensations were identified and positions/velocities measured
- Self-calibration solution intervals
- Explosion-center determination details and streamer position table
- Derivation of 90 yr rate (time span 15330 yr) in detail
- Dust temperature/opacity choice details for N source mass

## Analysis recipe

1. **Image continuum and CO(2-1)**: TCLEAN imaging after phase self-calibration  
  > "The data was imaged using the routine `TCLEAN` with the Robust parameter set equal to $+$0.5" (2 Observations)
   - software: CASA
   - parameter: robust 2.0 continuum, 0.5 line  
  > "We used a robust equals to 2.0 in `TCLEAN`." (2 Observations)
   - fitting: _not stated_
   - validation: Compared rms to theoretical (~0.08 mJy/beam)  
  > "approximately 0.08 mJy beam$^{-1}$" (2 Observations)
2. **Fit Gaussians to continuum sources and estimate dust mass**: Gaussian fits; optically thin dust mass from flux density  
  > "we assume optically thin emission, a grain opacity of 0.897 cm$^2$g$^{-1}$" (3 Results)
   - software: CASA
   - assumption: gas-to-dust 100, T 75-150 K, beta=1.1  
  > "a gas-to-dust ratio of 100, and a temperature ranging from 75–150 K" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Trace CO streamers and kinematic age**: Positions of CO condensations per channel; radial velocity vs distance; age = distance/velocity  
  > "taking an average radial velocity of 40 km s$^{-1}$, and a distance of 3$''$ or $\sim$6000 au, we obtain 700 yrs" (3 Results)
   - assumption: streamers mostly near plane of sky  
  > "it is likely that most of the motion is close to the plane of the sky" (3 Results)
   - fitting: _not stated_
   - validation: Second estimate 800 yr from southernmost streamer  
  > "consistent with the time (800 yr) obtained from the position most southern streamer" (3 Results)
4. **Outflow mass, momentum, energy**: Optically thin LTE CO(2-1)  
  > "Taking a distance of 2.03 kpc, an excitation temperature of 30 K, a ratio between the molecular hydrogen, and the carbon monoxide of 10$^4$" (3 Results)
   - assumption: Tex 30 K, H2/CO 1e4, 120 km/s range  
  > "a range of velocities of 120 km s$^{-1}$" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
5. **Galactic event rate**: Six known explosive outflows, time span 15330 yr, circle radius 2.8 kpc, disk radius 15 kpc  
  > "We adopt a time span of 15330 years between all 6 outflows" (4 Discussion)
   - fitting: _not stated_
   - validation: Compared with supernova rate and massive star formation rate  
  > "we get a massive star formation rate of 1 star every 50 yrs" (4 Discussion)

## Software

- **CASA** 6.4.1.12: Calibration, imaging, analysis  
  > "To calibrate, image, and analyze the ALMA data we used the Common Astronomy Software Applications (CASA) package, Version 6.4.1.12." (2 Observations)
- **astropy** : Python analysis routines  
  > "CASA (CASA Team et al. 2022) and astropy (The Astropy Collaboration 2013, 2018, 2022)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Kinematic age of outflow | 700 | not stated | yr | 3 | we obtain 700 yrs |
| Outflow mass | 7 | not stated | Msun | 4 | we obtain a mass of 7 M$_\odot$ |
| Kinetic energy | 1e48 | not stated | erg | 4 | a kinetic energy of 10$^{48}$ erg |
| Shell mass | 12.2-25.3 | not stated | Msun | 2 | we obtain a shell mass ranging between 12.2 to 25.3 M$_\odot$ |
| IRAS12326-S integrated flux | 1.87 | 0.02 | Jy | 2 | we obtain an integrated flux of 1.87 $\pm$ 0.02 Jy |
| IRAS12326-N integrated flux | 138.1 | 10 | mJy | 2 | we obtain an integrated flux of 138.1 $\pm$ 10 mJy |
| Galactic explosive outflow rate | one every 90 | not stated | yr | 5 | we estimate an updated rate of events of one every 90 years |

## Qualitative findings

- Over 10 CO streamers with Hubble-like expansion point to center of a newly found dusty shell  
  > "We find over 10 molecular and collimated well-defined streamers, with Hubble-Lemaitre like expansion motions" (abstract)

## Claim tuples

- H: IRAS 12326-6245 hosts an explosive outflow | E: ALMA 12CO(2-1) streamer mapping and velocity-distance plot | R: 10 streamers pointing to shell center with linear velocity-distance relation | F: A new explosive outflow, age ~700 yr, energy 1e48 erg | **supported**
- H: Explosive events occur at a rate comparable to massive star formation | E: Rate from six known outflows | R: One event per 90 yr | F: Similar to massive star formation and supernova rates | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Explosion center uncertain due to few streamers  
  > "we were not able to do a more complete statistical analysis to find the sky center of the explosion due to the low number of explosive streamers" (3 Results)
- Limitation (authors): Mass is a lower limit since CO likely optically thick  
  > "more likely the emission is optically thick at these millimeter wavelengths, so this estimation should be considered a lower limit" (3 Results)
- Caveat (inferred, ours): Streamer identification subjective; no uncertainties on age
- Caveat (inferred, ours): Distance uncertainty (+0.77/-0.61 kpc) not propagated
- Caveat (inferred, ours): Rate based on only six sources with ambiguous time span
- Caveat (inferred, ours): Continuum rms 10x above theoretical

## Reproducibility

- Data public (paper): Retrieved from ALMA archive  
  > "The ALMA observations were retrieved from [The Science Archive](https://almascience.nrao.edu/aq/)." (2 Observations)
- Products in archive: _not stated_
- Missing: Streamer position/velocity tables
- Missing: Cleaning parameters
- Missing: Self-cal details
- Data volume (inferred): ~100-200 GB
- Score (inferred): 4/5, Public data and basic imaging stated, but streamer identification is manual and parameters are missing.
- Rediscovery candidate: no, Key results depend on subjective streamer selection and unstated parameters.

## Links

- Method: (cite: 2020Cortes) (LTE outflow mass equation)
- Companion: (cite: 2022GuzmanCcolque) (Similar explosive outflow analysis and rate)
- Related: ALMA survey of six high-velocity-wing sources, 2016.1.01347.S

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
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
  "stated": 45,
  "rate": 0.608
 },
 "evidence_ok": true
}
```
