# An Asymmetric Keplerian Disk Surrounding the O-type Protostar IRAS 16547-4247

`2019ApJ...872..176Z` | The Astrophysical Journal 2019 | first author: Zapata, Luis A. | arXiv: 1901.04896 | DOI: 10.3847/1538-4357/aafedf

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Is there a resolved Keplerian disk around the O-type protostar IRAS 16547-4247 (IRAS 16547-E), and what is its enclosed mass and structure?  
  > "we carried out new ALMA observations with a high angular resolution at 0.85 mm (∼ 0.05 [′′] ) and a very good sensitivity to disclose the innermost structure of the disk candidate" (1. INTRODUCTION)
- Target **IRAS 16547-4247 (IRAS 16547-E and IRAS 16547-W)**: coordinates IRAS 16547-W: RA(J2000) 16h58m17.06s, Dec -42d52m07.285s  
  > "the distance of IRAS 16547−4247 of 2.9±0.6 kpc" (2. OBSERVATIONS); "The position of IRAS16547-W is at α(2000) = 16 [h] 58 [m] 17. [s] 06 ±" (3. RESULTS AND DISCUSSION); z/distance 2.9±0.6 kpc  
  > "the distance of IRAS 16547−4247 of 2.9±0.6 kpc" (2. OBSERVATIONS); "The position of IRAS16547-W is at α(2000) = 16 [h] 58 [m] 17. [s] 06 ±" (3. RESULTS AND DISCUSSION); distance from Rodríguez et al. 2018  
  > "the distance of IRAS 16547−4247 of 2.9±0.6 kpc" (2. OBSERVATIONS); "The position of IRAS16547-W is at α(2000) = 16 [h] 58 [m] 17. [s] 06 ±" (3. RESULTS AND DISCUSSION)

## Data provenance

- ALMA projects: 2016.1.00992.S
- bands: Band 7 (0.85 mm)  
  > "were carried out with ALMA at Band 7 in 2017 August 21 and 22" (2. OBSERVATIONS)
- frequencies and spectral setup: four spws (1.875, 0.937, 0.468, 0.468 GHz wide) centered at 353.684, 351.644, 339.160, 340.405 GHz; channels 0.430 (CH3OCHO), 0.321 (SO2), 0.215 (CS) km/s  
  > "centered at rest frequencies: 353.684 GHz (spw0), 351.644 GHz (spw1), 339.160 GHz (spw2), and 340.405 GHz (spw3), which cover a total bandwidth of 3.748 GHz." (2. OBSERVATIONS)
- continuum bandwidth: 3.748 GHz total, line-free channels  
  > "which cover a total bandwidth of 3.748 GHz." (2. OBSERVATIONS)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 21 to 3696.5 m (24.7–4348.8 kλ), 44 antennas of 12 m  
  > "Both observations used 44 antennas with a diameter of 12 m, yielding baselines with projected lengths from 21 to 3696.5 m (24.7–4348.8 kλ)." (2. OBSERVATIONS)
- angular resolution: continuum 0.06"×0.05" (PA +82.9°); lines 0.09"×0.07" (PA −76.7°)  
  > "angular resolution of 0. [′′] 06 × 0. [′′] 05 with a PA = +82.9 [◦]" (2. OBSERVATIONS)
- max recoverable scale: 0.87" (~2500 au)  
  > "The maximum recoverable scale for this ALMA observation is 0. [′′] 87 (∼ 2500 au)." (2. OBSERVATIONS)
- sensitivity: continuum rms 1.0 mJy/beam; line rms 10 mJy/beam km/s  
  > "The resulting image rms noise for the continuum was 1.0 mJy beam [−][1]" (2. OBSERVATIONS)
- time on source: about 1.6 h on-source; 2.5 h calibration  
  > "The integration time on-source was about 1.6 h, and 2.5 h was used for calibration." (2. OBSERVATIONS)
- observing dates: 2017 August 21 and 22  
  > "were carried out with ALMA at Band 7 in 2017 August 21 and 22" (2. OBSERVATIONS)
- pi or archival as stated: _not stated_
- Line: CS 7-6 v=1 (340397.96 MHz)
- Line: SO2 v=0 30(2,28)-29(3,27) A (340316.41 MHz)
- Line: CH3OCHO 37(13,25)-37(12,26) A v=0 (339548.47 MHz)
- External data: Distance 2.9±0.6 kpc  
  > "of IRAS 16547−4247 of 2.9±0.6 kpc (Rodr´ıguez et al. 2018)" (2. OBSERVATIONS) [from Rodríguez et al. 2018]
- External data: LSR systemic velocity −30.6 km/s  
  > "The LSR systemic radial velocity of IRAS 16547-E is −30.6 km s [−][1] (Garay et al. 2003)." (3. RESULTS AND DISCUSSION) [from Garay et al. 2003]
- External data: Dust opacity 0.020 cm2/g at 0.85 mm  
  > "Assuming a dust mass opacity (κ ν ) of 0.020 cm [2] g [−][1] (taking a gas-to-dust ratio of 100)" (A. DUST MASS ESTIMATION) [from Ossenkopf et al. 1994]
- External data: Dust temperature 250 K  
  > "a characteristic dust temperature (T d ) of 250 K (Hern´andez-Hern´andez et al. 2014)" (A. DUST MASS ESTIMATION) [from Hernández-Hernández et al. 2014]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1617-5848  
  > "J16175848 was also used for the flux amplitude calibration." (2. OBSERVATIONS)
- flux scale uncertainty: _not stated_
- self calibration: phase and amplitude self-calibration using continuum image as model; solutions applied to line data  
  > "We self-calibrated in phase and amplitude using the resulting mm continuum image as model." (2. OBSERVATIONS)

### Imaging

- task: CASA CLEAN  
  > "Imaging of the calibrated visibilities was done using the task CLEAN." (2. OBSERVATIONS)
- deconvolver: _not stated_
- weighting robust: robust = −2.0 continuum, +0.5 lines  
  > "We used the ROBUST parameter of CLEAN in CASA set to −2.0 in the continuum and +0.5 for the line im" (2. OBSERVATIONS)
- uv taper: high-resolution continuum image uses baselines ≥ 900 kλ  
  > "constraining the uvrange (baselines ≥ 900 kλ)" (3. RESULTS AND DISCUSSION)
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
- final rms: continuum 1.0 mJy/beam; line 10 mJy/beam km/s  
  > "noise was 10 mJy beam [−][1] km s [−][1] at an angular resolution of 0. [′′] 09 × 0. [′′] 07" (2. OBSERVATIONS)

### Inherited from earlier work

- Thin Keplerian+infall disk model fitting procedure  
  > "Using a similar procedure as that described in Estalella et al. (2012) and S´anchez-Monge et al. (2013)" (B. KEPLERIAN THIN DISK MODEL) [from Estalella et al. 2012; Sánchez-Monge et al. 2013]
- Model assumes optically thin emission with single temperature and density  
  > "As described in Girart et al. (2014), the model assumes that the intensity of the disk is directly proportional to the" (B. KEPLERIAN THIN DISK MODEL) [from Girart et al. 2014]

### Not stated but needed to reproduce (our reading)

- CASA version
- Calibration pipeline vs manual and flux scale uncertainty
- Image size, cell size, deconvolver, masks, clean threshold
- Line-free channels for continuum and continuum subtraction
- Self-calibration solution intervals
- Starting guesses and parameter grid for model fit
- Moment map clipping thresholds
- Number of data points used in chi2 and which channels
- Flux density of J1617-5848

## Analysis recipe

1. **Image continuum and lines**: CLEAN with self-calibration on continuum; solutions applied to lines  
  > "We then applied the solutions for self-calibration of the continuum to the" (2. OBSERVATIONS)
   - software: CASA
   - parameter: robust −2.0 continuum, +0.5 lines  
  > "set to −2.0 in the continuum and +0.5 for the line im" (2. OBSERVATIONS)
   - fitting: _not stated_
   - validation: _not stated_
2. **Moment maps and PV diagrams**: Moment 0/1 maps; PV diagrams along disk major axis PA=50° compared with Keplerian curves for 10, 20, 30 Msun  
  > "we computed Position-Velocity (PV) diagrams along the major axis of this disk (PA=50 [◦] )" (3. RESULTS AND DISCUSSION)
   - software: CASA, KARMA
   - assumption: inclination 55°  
  > "We assume an inclination angle for the disk of 55 [◦] ." (Figure 3 caption)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit thin Keplerian disk model to CH3OCHO**: Thin disk with Keplerian rotation and infall; parameter space searched for minimum rms residual over channel maps  
  > "the m-dimensional parameter space is searched for the minimum of the rms fit residual for all the channel maps." (B. KEPLERIAN THIN DISK MODEL)
   - software: thin disk model by R. Estalella
   - parameter: fixed: beam-width 0.06", inner radius 0.005"; power-law indices 0.5 (rotation, infall), 1.0 (intensity)  
  > "Inner Disk Radius (r 1 ) 0.005 [′′] (fixed)" (Table 1)
   - assumption: optically thin emission; single temperature and density  
  > "the emission is optically thin, and that the density and temperature are described by a single temperature and density, respectively." (B. KEPLERIAN THIN DISK MODEL)
   - fitting: Minimum chi2; 1σ errors (α=0.68) from rms residual increase factor [1+Δ/(n−m)]^1/2  
  > "α is the significance level, α = 0.68 (equivalent to 1σ for a Gaussian error distribution)." (B. KEPLERIAN THIN DISK MODEL)
   - validation: Model and data PV diagrams along 50° and 140° compared  
  > "From these two images we find a good correspondence between our model and the data." (3. RESULTS AND DISCUSSION)
4. **Dust masses of continuum sources**: Optically thin isothermal dust mass from Gaussian-fit flux density  
  > "Assuming that the dust emission is optically thin and isothermal, the dust mass (M d ) is directly proportional to the" (A. DUST MASS ESTIMATION)
   - parameter: S=1.05 Jy (E), 0.020 Jy (W)  
  > "for flux densities estimated from a Gaussian fit for IRAS16547-E of 1.05 Jy, and for IRAS16547-W of 0.020 Jy" (A. DUST MASS ESTIMATION)
   - assumption: kappa=0.020 cm2/g, gas-to-dust 100, Td=250 K, D=2.9 kpc  
  > "as well as a characteristic dust temperature (T d ) of 250 K" (A. DUST MASS ESTIMATION)
   - fitting: _not stated_
   - validation: Lower limits; uncertainty up to factor 4 from opacity and temperature  
  > "The actual uncertainty could be very large (a factor of up to 4)" (A. DUST MASS ESTIMATION)

## Software

- **CASA** : calibration, imaging, analysis  
  > "The data were calibrated, imaged, and analyzed using" (2. OBSERVATIONS)
- **KARMA** : data analysis  
  > "To analyze the data, we also used the KARMA (Gooch et al. 1996) package." (2. OBSERVATIONS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Enclosed mass (Keplerian fit) | 25 | ±3.0 | Msun | 3 | Enclosed Mass 25 ± 3.0 M ⊙ |
| Disk inclination | 55 | ±5.0 | deg | 3 | Inclination Angle (i) 55 [◦] ± 5.0 [◦] |
| Outer disk radius | 0.3 arcsec (1190 au) | ±0.1 arcsec (±290 au) | arcsec | 3 | the size 0.3 [′′] ±0.1 [′′] (1190±290 au) |
| Central velocity of disk | -30.1 | ±0.5 | km/s | 3 | Central velocity of the Disk (v 0 ) −30.1±0.5 km s [−][1] |
| Dust mass envelope IRAS16547-E | 3.55 | ±0.05 | Msun | 4 | of the dusty envelope in IRAS16547-E of 3.55±0.05 M ⊙ |
| Central star mass | ~20 | not stated | Msun | 4 | we estimated a mass of about 20 M ⊙ for the central star. |
| Binary separation (A-B) | 0.1 arcsec (300 au) | not stated | arcsec | 0 | The binary sources are separated about 0.1 [′′] or 300 au in projection |

## Qualitative findings

- Disk shows asymmetries, possibly fragmentation or excitation differences; binary orientation is orthogonal to disk axis  
  > "It is interesting to note that the binary orientation is orthogonal to the CH 3 OCHO molecular disk axis" (3. RESULTS AND DISCUSSION)

## Claim tuples

- H: Does IRAS 16547-E host a resolved Keplerian disk? | E: PV diagrams and thin-disk model fit to CH3OCHO and CS | R: Velocities consistent with Keplerian rotation; enclosed mass 25±3 Msun | F: A Keplerian disk surrounds the O-type protostar | **supported**
- H: Is the central source a binary? | E: Continuum image with uv ≥ 900 kλ | R: Two sources A and B separated 0.1" | F: Binary of compact dusty objects at disk center | **supported**

## Reasoning

- Why this data: High-energy transitions trace the compact disk  
  > "Zapata et al. (2015) noted that high-energy transitions (E u ≥ 500 K) seem to trace mostly the compact disk." (3. RESULTS AND DISCUSSION)
- Why this method: _not stated_
- Alternative: Two offset non-Keplerian rings in CS rejected since the enclosed mass of the outer ring should be larger  
  > "We conclude that this interpretation must be incorrect because the enclosed mass from the exterior ring should be larger." (3. RESULTS AND DISCUSSION)
- How they decided it was enough: _not stated_
- Limitation (authors): CH3OCHO and CS likely optically thick at center, so model inner radius may be an opacity effect  
  > "so the inner disk radius found in the model could be due only to opacity effects." (B. KEPLERIAN THIN DISK MODEL)
- Caveat (inferred, ours): Fit is rms-based with many fixed parameters; no posterior
- Caveat (inferred, ours): Resolution comparable to disk scales; asymmetric emission may bias mass
- Caveat (inferred, ours): Outflow/envelope contamination of the disk emission
- Caveat (inferred, ours): Dust masses are lower limits with a large systematic factor

## Reproducibility

- Data public (paper): Project 2016.1.00992.S named in acknowledgements; public status not explicitly stated  
  > "This paper makes use of the following ALMA data:" (3. RESULTS AND DISCUSSION)
- Products in archive: _not stated_
- Code: Thin disk model documented at a URL (Estalella); no code released otherwise  
  > "We have used the model of a thin disk with a Keplerian and infall kinematics made by Robert Estalella" (B. KEPLERIAN THIN DISK MODEL)
- Missing: CASA version and calibration details
- Missing: Imaging parameters beyond robust
- Missing: Disk model code and starting guesses
- Data volume (inferred): ~100-300 GB raw for two Band 7 execution blocks
- Score (inferred): 5/5, Data are identified and key parameters given, but CASA version, imaging and fitting details are missing.
- Rediscovery candidate: no, Imaging and model-fitting recipe incomplete, so the results are hard to redo exactly.

## Links

- Method: Estalella et al. 2012; Sánchez-Monge et al. 2013 (Thin disk fitting procedure)
- Companion: Zapata et al. 2015 (Earlier ALMA observations of IRAS 16547-4247)

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
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
  "facts": 73,
  "stated": 46,
  "rate": 0.63
 },
 "evidence_ok": true
}
```
