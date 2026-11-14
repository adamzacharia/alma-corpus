# Planet Formation in AB Aurigae: Imaging of the Inner Gaseous Spirals Observed inside the Dust Cavity

`2017ApJ...840...32T` | The Astrophysical Journal 2017 | first author: Tang, Ya-Wen | arXiv: 1704.02699 | DOI: 10.3847/1538-4357/aa6af7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the gas and dust structures inside the AB Aur dust cavity at 0.1" resolution, and do the CO spirals imply embedded companions?  
  > "we obtained ALMA observing time in Cycle 3 to image at very high angular resolution ($< 0.1''$) the close environment of AB Aur in CO and in mm continuum." (Introduction)
- Target **AB Aurigae**: coordinates 1.3 mm continuum peak (04:55:45.85, 30:33:04.30), epoch J2000  
  > "Located at 140 pc, AB Aurigae (hereafter AB Aur) is one of the closest Herbig Ae stars of spectral type of A0 Ve" (Introduction); "which is at ($\alpha$, $\delta$) = (04:55:45.85, 30:33:04.30)" (Observations); z/distance 140 pc (GAIA DR1: 153±10 pc)  
  > "Located at 140 pc, AB Aurigae (hereafter AB Aur) is one of the closest Herbig Ae stars of spectral type of A0 Ve" (Introduction); "which is at ($\alpha$, $\delta$) = (04:55:45.85, 30:33:04.30)" (Observations); distance from assumed for comparison with previous work; Gaia DR1 noted  
  > "Located at 140 pc, AB Aurigae (hereafter AB Aur) is one of the closest Herbig Ae stars of spectral type of A0 Ve" (Introduction); "which is at ($\alpha$, $\delta$) = (04:55:45.85, 30:33:04.30)" (Observations)

## Data provenance

- ALMA projects: 2015.1.00889.S
- bands: 1.3 mm continuum, 12CO J=2-1  
  > "images in $^{12}$CO (J=2-1) emission and in dust continuum at the wavelength of 1.3 mm" (abstract)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m antennas, 45 and 46 per execution block  
  > "The array included 45 and 46 of the 12-m antennas, respectively." (Observations)
- configurations: _not stated_
- baselines: 78.1 m to 15.5 km  
  > "The baselines ranged from 78.1 m to 15.5 km." (Observations)
- angular resolution: ~0.1" (14 au); CO beam 0.11"x0.08"; continuum beam 0.14"  
  > "sensitivity of 1.60 mJy per 0$\ensuremath{''}$11$\times$0$\ensuremath{''}$08 beam (4.6 K)" (Observations)
- max recoverable scale: ~2.1"  
  > "the missing 80% of the flux is at the scale larger than 2$\ensuremath{''}$1, which is determined by the shortest baseline of our observation" (Continuum Emission)
- sensitivity: CO 1.60 mJy/beam (0.71 km/s channels); continuum 33 µJy/beam  
  > "The effective sensitivity (1$\sigma$, including dynamic range limitations) of the continuum emission is 33 $\mu$Jy per 0$\ensuremath{''}$14 beam (0.04 K)." (Observations)
- time on source: _not stated_
- observing dates: Nov. 5 and Nov. 10, 2015  
  > "with two execution blocks on Nov. 5 and Nov. 10, 2015, respectively." (Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Line: C18O 3-2 (non-detection) (not stated)
- External data: Earlier IRAM + 30-m 1.3 mm continuum flux of 80 mJy and central 1.3 mJy  
  > "reported flux density of 80 mJy at 1.3 mm from our previous detection with shorter baselines (cite: tang2012)" (Continuum Emission) [from (cite: tang2012)]
- External data: Stellar position and proper motion  
  > "proper motion with value of (2.63, -24.73) mas yr$^{-1}$ given by (cite: 2007Leeuwen)" (Observations) [from (cite: 2007Leeuwen)]
- External data: 3.3 cm jet emission (0.8 mJy at 7 mm)  
  > "The total flux density of the jet is reported to be 0.8 mJy at 7 mm." (Continuum Emission) [from (cite: rodriguez2014)]

## Processing

### Calibration

- pipeline or manual: Calibrated by EA ARC, standard calibration  
  > "The calibrations were done by EA ARC using CASA 4.5." (Observations)
- casa version: CASA 4.5  
  > "The calibrations were done by EA ARC using CASA 4.5." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120 (0.77 Jy) and J0510+1800 (3.42 Jy)  
  > "The absolute flux level is referenced to J0423-0120 and J0510+1800 for which flux densities of 0.77 Jy and 3.42 Jy, respectively" (Observations)
- flux scale uncertainty: 10%  
  > "The flux calibration is expected to be accurate at the 10% level." (Observations)
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
- final beam: CO 0.11"x0.08"; continuum 0.14"  
  > "sensitivity of 1.60 mJy per 0$\ensuremath{''}$11$\times$0$\ensuremath{''}$08 beam (4.6 K)" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Gas temperature of 140 K for CO at 30 au  
  > "following (cite: Pietu+etal_2005), we assume CO traces gas at a temperature of 140 K" (General Features) [from (cite: Pietu+etal_2005)]
- Systemic velocity 5.85 km/s  
  > "using the systemic velocity, $v_{\rm sys}$, of 5.85 km s$^{-1}$ from (cite: tang2012)" (Kinematics) [from (cite: tang2012)]
- Ring parameters from 0.9 mm observations  
  > "More precise values of the ring parameters are actually derived from higher sensitivity, lower angular resolution observations at 0.9 mm (Tang et al., in prep)." (Continuum Emission) [from Tang et al., in prep]

### Not stated but needed to reproduce (our reading)

- tclean/imaging parameters (weighting, robust, cell size, image size, deconvolver)
- GILDAS imaging details and clean masks
- spectral windows and rest frequencies
- continuum-subtraction line-free channels
- self-calibration details
- spiral maximum-extraction and fit procedure/uncertainties
- visibility-model fit details for central continuum
- spectral window for C18O 3-2 (different band) data source
- stellar mass derivation

## Analysis recipe

1. **Calibrate and export**: Standard calibration by EA ARC, then exported to GILDAS; proper motion corrected and shifted to epoch 2000.0  
  > "After calibration, the data were exported to the GILDAS package for further analysis." (Observations)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: Secondary calibrator J0518+3306 position offsets 0.019" and 0.036"; positional accuracy ~0.03"  
  > "We conclude that the absolute positioning accuracy of this experiment is limited to $\sim 0\ensuremath{''}03$." (Observations)
2. **Continuum measurement**: Model central continuum peak with elliptical disk in visibility plane; measure ring and total flux  
  > "We model the central continuum peak with an elliptical disk in the visibility plane." (Continuum Emission)
   - software: GILDAS
   - assumption: Free-free jet spectral index 0.6  
  > "Assuming a spectral index of 0.6 for the jet" (Continuum Emission)
   - fitting: _not stated_
   - validation: Compared with previous IRAM flux  
  > "The flux density is 2.1 mJy, which is larger than the previous detected value of 1.3 mJy with the IRAM interferometer" (Results, Continuum Emission)
3. **Missing flux estimate**: Smooth CO to 0.56"x0.42" and compare with Tang et al. 2012 including 30-m data  
  > "we are only recovering 25 % of the line flux in the velocity ($v_{\rm LSR}$) range of 2 to 5 and 7 to 10 km/s." (CO Gas)
   - fitting: _not stated_
   - validation: _not stated_
4. **Spiral fitting**: Deproject moment 0 map, take maxima every 5 deg in azimuth, fit logarithmic spirals  
  > "We then take the maximum locations of the $^{12}$CO moment 0 image every 5$\ensuremath{^\circ}$ in azimuth angle, $\theta$." (General Features)
   - parameter: inclination 23.2 deg, rotation axis PA -36 deg  
  > "the moment 0 map is deprojected with an inclination of 23.2$\ensuremath{^\circ}$" (General Features)
   - fitting: logarithmic spiral least-squares fit (method not stated)  
  > "We first fit the eastern and western arm with logarithmic spirals in order to search for the best description." (Results, CO Gas, General Features)
   - validation: _not stated_
5. **Kinematics**: Extract PV plots along spirals and compare with Keplerian velocity  
  > "We extracted the position-velocity plots along the best-fit spirals" (Kinematics)
   - parameter: M* = 2.4 Msun, vsys 5.85 km/s, i 23.2 deg  
  > "a stellar mass, $M_{\star}$, of 2.4 $M_{\ensuremath{\odot}}$ and P.A. of the rotation axis of -36$\ensuremath{^\circ}$, using the systemic velocity, $v_{\rm sys}$, of 5.85 km s$^{-1}$" (Results, Kinematics)
   - fitting: _not stated_
   - validation: No radial motion detected  
  > "There is no radial motion detected within the resolution of the reported observations" (Results, CO Gas, Kinematics)
6. **Gas mass estimate**: Optically thin CO column from peak TB, T=140 K, linewidth 1 km/s, CO/H2 = 1e-4  
  > "for a CO gas abundance of 10$^{-4}$ with respect to H$_2$, gives a total gas mass of 0.03 $M_{\Earth}$ in one beam." (General Features)
   - assumption: CO/C18O = 560  
  > "abundance ratio of CO to C$^{18}$O of 560" (General Features)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5: Calibration by EA ARC  
  > "The calibrations were done by EA ARC using CASA 4.5." (Observations)
- **GILDAS** : Further analysis after calibration  
  > "After calibration, the data were exported to the GILDAS package for further analysis." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total detected continuum flux density | 16.4 | not stated | mJy | 2 | The total detected flux density is 16.4 mJy |
| Central continuum flux density | 2.1 | not stated | mJy | 2 | The flux density is 2.1 mJy |
| Central disk diameter | ~11 | not stated | au | 2 | The best fit disk diameter is found to be $\sim 11$ au. |
| Eastern spiral fit | r = 0.85" exp(-21.0 theta) | not stated | arcsec, theta in deg | 4 | the best-fit function is $r(\theta)=0.85\ensuremath{''} \exp(-21.0\theta)$ |
| Western spiral fit | r = 0.38" exp(-12.5 theta) | not stated | arcsec, theta in deg | 4 | the best fit function is $r(\theta) = 0.38\ensuremath{''}\exp(-12.5 \theta)$ |
| Peak CO brightness temperature at P1 | 70 | not stated | K | 0 | the peak brightness temperature, $T_{\rm B}$, of 70 K at $V_{\rm LSR}$ of 8.32 km/s |
| CO gas mass per beam at P1 (lower limit) | 0.03 | not stated | Earth masses | 6 | gives a total gas mass of 0.03 $M_{\Earth}$ in one beam |
| Recovered CO line flux | 25 | not stated | % | 3 | we are only recovering 25 % of the line flux |

## Qualitative findings

- CO emission is dominated by two trailing spirals inside the dust ring, with Keplerian kinematics  
  > "These spirals are trailing and appear to be about 4 times brighter than their surrounding medium." (abstract)

## Claim tuples

- H: Do gaseous spirals exist inside the AB Aur dust cavity? | E: ALMA 12CO 2-1 at ~0.1" resolution | R: Two spirals within 90 au, ~12 sigma, Keplerian kinematics | F: First detection of gaseous spirals inside the dust gap | **supported**
- H: Are the spirals driven by embedded companions? | E: Compare spiral shape and location with planet-disk models | R: Candidate planets at ~30 au and/or 60-80 au; large pitch angle hard to explain | F: Planets most likely trigger spirals, but pitch angle puzzling | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gravitational instability, shadows from tilted inner disk, and asymmetric accretion considered less likely  
  > "so this mechanism is unlikely to apply to our case." (Discussions)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing flux on scales >2.1" affects spiral morphology and contrast  
  > "it may be affected by differential filtering of the extended emission at the various velocities" (Discussions)
- Caveat (inferred, ours): No uncertainties on spiral fits
- Caveat (inferred, ours): Missing flux unquantified for morphology
- Caveat (inferred, ours): Planet masses scaled from a single model
- Caveat (inferred, ours): Free-free contamination of continuum

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: GILDAS scripts
- Missing: Fit uncertainties
- Data volume (inferred): ~100-200 GB raw for two long-baseline execution blocks
- Score (inferred): 3/5, Project code given but imaging and fitting details are sparse.
- Rediscovery candidate: no, Imaging recipe is incomplete.

## Links

- Companion: (cite: tang2012) (Previous IRAM observations of AB Aur)

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 41,
  "rate": 0.539
 },
 "evidence_ok": true
}
```
