# Brown Dwarf Disks with ALMA

`2014ApJ...791...20R` | The Astrophysical Journal 2014 | first author: Ricci, L. | arXiv: 1406.0635 | DOI: 10.1088/0004-637X/791/1/20

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What are the sizes, dust structure and grain sizes of disks around three young brown dwarfs/very low mass stars in Taurus, and what do they imply for BD formation and planet formation?  
  > "We analyze the continuum visibilities and constrain the disks physical structure in dust." (abstract)
- Target **2M0444**: coordinates 2MASS J04442713+2512164  
  > "2M0444 (2MASS J04442713+2512164)" (2 ALMA Observations); "at the Taurus distance of 140 pc" (3.1 Continuum maps and visibilities); z/distance 140 pc (Taurus)  
  > "2M0444 (2MASS J04442713+2512164)" (2 ALMA Observations); "at the Taurus distance of 140 pc" (3.1 Continuum maps and visibilities); distance from assumed Taurus distance  
  > "2M0444 (2MASS J04442713+2512164)" (2 ALMA Observations); "at the Taurus distance of 140 pc" (3.1 Continuum maps and visibilities)
- Target **CIDA 1**: coordinates 2MASS J04141760+2806096  
  > "CIDA 1 (2MASS J04141760+2806096)" (2 ALMA Observations); z/distance 140 pc (Taurus)  
  > "CIDA 1 (2MASS J04141760+2806096)" (2 ALMA Observations); distance from assumed Taurus distance  
  > "CIDA 1 (2MASS J04141760+2806096)" (2 ALMA Observations)
- Target **CFHT Tau 4**: coordinates 2MASS J04394748+2601407  
  > "CFHT Tau 4 (2MASS J04394748+2601407)" (2 ALMA Observations); z/distance 140 pc (Taurus)  
  > "CFHT Tau 4 (2MASS J04394748+2601407)" (2 ALMA Observations); distance from assumed Taurus distance  
  > "CFHT Tau 4 (2MASS J04394748+2601407)" (2 ALMA Observations)

## Data provenance

- ALMA projects: 2011.0.00259.S
- bands: Band 7 (~338 GHz, 0.89 mm) and Band 3 (~93 GHz, 3.2 mm), Cycle 0  
  > "using ALMA Early Science in Cycle 0 at Band 7 and 3 (about 338 and 93 GHz, respectively)" (2 ALMA Observations)
- frequencies and spectral setup: 4 spectral windows, 1.875 GHz each, 0.488 MHz channels; Band 7 centered 331.102, 332.998, 343.102, 344.998 GHz; Band 3 86.102, 87.998, 98.103, 99.998 GHz  
  > "Spectral windows were centered at 331.102, 332.998, 343.102, 344.998 GHz for Band 7 observations and 86.102, 87.998, 98.103, 99.998 GHz for Band 3." (2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Extended array, 25 or 26 antennas  
  > "All observations were performed with either 25 or 26 antennas in the Extended array configuration" (2 ALMA Observations)
- baselines: up to ~400 m (15.1-402.3 m)  
  > "which provides projected baseline lengths up to $\sim$400 m" (2 ALMA Observations)
- angular resolution: ~0.40 arcsec at Band 7 (about 28 AU in radius); Band 3 poorer by 3.6  
  > "the angular resolution is poorer by a factor of $\approx 338/93 = 3.6$ because of the lower frequency" (3.1 Continuum maps and visibilities)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Band 7: 9 min CIDA 1 and CFHT Tau 4, 5 min 2M0444; Band 3: 15 min CIDA 1 and 2M0444, 55 min CFHT Tau 4  
  > "9 minutes for CIDA 1 and CFHT Tau 4 and 5 minutes for 2M0444 in Band 7; 15 minutes for CIDA 1 and 2M0444 and 55 minutes for CFHT Tau 4 in Band 3." (2 ALMA Observations)
- observing dates: 2012 Aug 27 (Band 7); 2012 Nov 18, 19, 20 (Band 3)  
  > "2012 Aug 27 | CIDA 1, 2M0444, CFHT Tau 4 | 7 | Ganymede | 25" (Table 1)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (not stated)
- External data: Stellar properties (Teff, L, M) for the three sources  
  > "The derivation of the other stellar parameters is described in (cite: Ricci:2013) for 2M0444 and (cite: Andrews:2013) for CIDA 1 and CFHT Tau 4." (Table 4 notes) [from (cite: Ricci:2013); (cite: Andrews:2013)]
- External data: Spectral types  
  > "Spectral types are from (cite: Luhman:2010)." (Table 4 notes) [from (cite: Luhman:2010)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 3.4.0  
  > "The interferometric visibility data were calibrated with the 3.4.0 version of the CASA software package (cite: McMullin:2007)." (2 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede and Callisto (Butler-JPL-Horizons 2012 models); bandpass J0538-440; gain J0510+180  
  > "The flux scale was tied to the Butler-JPL-Horizons 2012 models of Ganymede and Callisto, resulting in an accuracy of $\sim10\%$." (2 ALMA Observations)
- flux scale uncertainty: ~10%  
  > "resulting in an accuracy of $\sim10\%$" (2 ALMA Observations)
- self calibration: Only for CIDA 1  
  > "Self-calibration could be performed only in the case of CIDA 1, which is the brightest among our sources." (2 ALMA Observations)

### Imaging

- task: CASA imaging; continuum map per band  
  > "Imaging of the calibrated visibilities was done in CASA." (2 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "a continuum map was produced using natural weighting and combining all the channels without line emission" (2 ALMA Observations)
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

- Visibility modeling procedure (two-layer disk models, MCMC fit)  
  > "We adopt a similar procedure as outlined in (cite: Isella:2009) and (cite: Ricci:2013)." (4 Analysis of the interferometric visibilities) [from (cite: Isella:2009); (cite: Ricci:2013)]
- Dust opacity model  
  > "Dust opacities are derived by using the same method as described in (cite: Ricci:2010a)." (4 Analysis of the interferometric visibilities) [from (cite: Ricci:2010a)]

### Not stated but needed to reproduce (our reading)

- Flux-integration regions and CASA clean parameters (cell, image size, masks, line-free channels)
- MCMC details: priors, walkers, chain length, convergence, code
- Ranges of free parameters and treatment of disk center/flux offsets
- Moment-map velocity range and clipping thresholds
- Which visibility data (Band 7 only) and binning used in fit; self-cal solint for CIDA 1
- Disk scale height/flaring parameters and exact dust composition fractions

## Analysis recipe

1. **Measure continuum fluxes and spectral index**: Integrate surface brightness of pixels with emission in natural-weighted maps; alpha from 338 and 93 GHz fluxes  
  > "obtained by integrating the surface brightness from each pixel with emission" (3.1 Continuum maps and visibilities)
   - software: CASA
   - fitting: _not stated_
   - validation: Uncertainties include map noise and 10% flux scale  
  > "the reported uncertainties account for both the noise level in the maps and the $10\%$ uncertainty on the determination of the absolute flux scale" (3.1 Continuum maps and visibilities)
2. **CO moment maps for geometry**: Moment 0 and 1 maps of CO(3-2); P.A. from axis joining blue- to red-shifted pixels; inclination ranges from maps  
  > "the P.A. of the disk was estimated from the angle of the axis joining the blue-shifted pixels to the red-shifted pixels in the moment 1 maps" (4 Analysis of the interferometric visibilities)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit Band 7 visibilities with disk models**: Two-layer flared disk models; surface density power law; model visibilities via Fourier transform compared at observed (u,v); chi2 with MCMC  
  > "We used a Markov Chain Monte Carlo (MCMC) to run large collections of disk models by varying the input parameters that our analysis aims to constrain." (4 Analysis of the interferometric visibilities)
   - software: MCMC (custom)
   - parameter: R_in = 0.05 AU; free parameters M_disk (Sigma_10AU), p, R_out  
  > "For the disk inner radius $R_{\rm{in}}$ we considered a value of 0.05 AU" (4 Analysis of the interferometric visibilities)
   - parameter: Grain size distribution n(a) ∝ a^3, amin 0.1 micron; T_ext = 10 K (5, 15 K tested); T ∝ R^-3/4 beyond R_thin  
  > "We chose a fiducial value for $T_{\rm{ext}} = 10$ K" (4 Analysis of the interferometric visibilities)
   - assumption: Distance 140 pc; gas-to-dust ratio 100; kappa 0.02 cm2/g_gas at 0.89 mm  
  > "The ISM-like value of 100 for the gas-to-dust mass ratio is also assumed." (Table 5 notes)
   - fitting: chi2 minimization with MCMC; 1 sigma confidence intervals  
  > "Intervals for each parameter are given at the $1\sigma$ confidence level." (Table 5 notes)
   - validation: Best-fit model visibilities compared with binned data; T_ext variations give consistent results  
  > "found best fit models with parameters which lie within the confidence intervals obtained in the 10 K case" (4 Analysis of the interferometric visibilities)
4. **Derive dust opacity index and grain sizes**: Constrain beta from models; relate to a_max via dust model  
  > "Our models constrain $\beta = 0.2 \pm 0.2$, $0.3 \pm 0.2$, $0.4 \pm 0.2$ for 2M0444, CIDA 1, CFHT Tau 4, respectively." (5.1 Large grains in disks around VLMs/BDs)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 3.4.0: calibration and imaging  
  > "calibrated with the 3.4.0 version of the CASA software package" (2 ALMA Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 7 flux 2M0444 | 9.0 | rms 0.2 mJy/beam | mJy | 1 | 2M0444 / 9.0 / 0.2 / 0.87 / 0.03 / 1.81 $\pm$ 0.11 |
| alpha 338-93 GHz CIDA 1 | 1.98 | 0.11 | dimensionless | 1 | CIDA 1 / 27.0 / 0.3 / 2.1 / 0.03 / 1.98 $\pm$ 0.11 |
| alpha 338-93 GHz CFHT Tau 4 | 2.04 | 0.13 | dimensionless | 1 | CFHT Tau 4 / 4.3 / 0.2 / 0.31 / 0.02 / 2.04 $\pm$ 0.13 |
| R_out 2M0444 | 139 | +20/-27 | AU | 3 | 2M0444 / 139 $^{+20}_{-27}$ / 1.65 $^{+0.07}_{-0.10}$ |
| R_out CIDA 1 | 66 | +14/-12 | AU | 3 | CIDA 1 / 66 $^{+14}_{-12}$ / 1.46 $^{+0.13}_{-0.21}$ |
| R_out CFHT Tau 4 | >80 | lower limit | AU | 3 | CFHT Tau 4 / $>$ 80 / 1.20 $^{+0.10}_{-0.45}$ |
| CO(3-2) flux 2M0444 | 0.98 | 0.03 | Jy km/s | 2 | derived flux values of $0.98 \pm 0.03$ and $1.45 \pm 0.05$ Jy$\cdot$km/s for 2M0444 and CIDA 1 |
| beta 2M0444 | 0.2 | 0.2 | dimensionless | 4 | $\beta = 0.2 \pm 0.2$, $0.3 \pm 0.2$, $0.4 \pm 0.2$ |
| Disk mass 2M0444 (x kappa/0.02) | 1.3 | +0.2/-0.2 | M_Jup | 3 | 1.3 $^{+0.2}_{-0.2}$ |

## Qualitative findings

- Disk sizes, p and mass ratios similar to disks around T Tauri stars, favoring stellar-like formation over ejection  
  > "lie within the ranges found for disks around young stars" (6 Summary)

## Claim tuples

- H: Brown dwarf disks are large, not compact optically thick | E: Visibility modeling of Band 7 data | R: R_out ~140, 70 AU and >80 AU | F: Disks are relatively large, similar to T Tauri disks | **supported**
- H: Mm-sized grains exist in BD disks | E: Spectral index and beta from model | R: alpha ~1.8-2.0, beta 0.2-0.4 | F: Grains of at least mm size present | **supported**
- H: BD formation via ejection predicts small disks | E: Compare R_out with simulations of Bate | R: Radii larger than predicted | F: Stellar-like collapse favored, with caveat on simulations and selection bias | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Small optically thick disks (R_out <~10 AU) cannot explain the low spectral indices  
  > "cannot be explained by small, $R_{\rm{out}} \mathbin{\lower 3pt\hbox
      {$\rlap{\raise 5pt\hbox{$\char'074$}}\mathchar"7218$}}10$ AU, optically thick disks" (5.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Sample biased toward brightest disks; dust opacity absolute values unconstrained  
  > "is also strongly biased toward the brightest disks which can be spatially resolved more easily at sub-mm wavelengths" (5.2)
- Caveat (inferred, ours): Band 3 visibilities not used in fit; beta depends on assumed dust model and T_ext
- Caveat (inferred, ours): Inclination/PA from low-resolution CO moment maps
- Caveat (inferred, ours): Gas-to-dust ratio assumed

## Reproducibility

- Data public (paper): ALMA Cycle 0 data cited by project code  
  > "ADS/JAO.ALMA#2011.0.00259.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Disk modeling/MCMC code and priors
- Missing: Imaging parameters
- Missing: Moment-map settings
- Data volume (inferred): ~10-30 GB raw
- Score (inferred): 3/5, Public data and clear model description, but modeling code and many parameters unstated.
- Rediscovery candidate: no, Fitting relies on custom code and inherited methods not fully specified.

## Links

- Method: (cite: Isella:2009) (visibility modeling procedure)
- Method: (cite: Ricci:2010a) (dust opacity method)
- Companion: (cite: Ricci:2012a) (first ALMA brown dwarf disk paper (rho Oph 102))
- Companion: (cite: Ricci:2013) (earlier 2M0444 SMA/CARMA analysis)

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
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 42,
  "rate": 0.583
 },
 "evidence_ok": true
}
```
