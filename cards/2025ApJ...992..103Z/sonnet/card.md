# Impact of Gravity on Changing Magnetic Field Orientations in a Sample of Massive Protostellar Clusters Observed with ALMA

`2025ApJ...992..103Z` | The Astrophysical Journal 2025 | first author: Zhang, Qizhou | arXiv: 2508.18538 | DOI: 10.3847/1538-4357/adfdcb

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: How do magnetic field orientations at 0.01 pc core scale and 10^3 au envelope scale relate in massive protostellar clumps, and what role does gravity play in changing them?  
  > "The relative orientations (ROs) of the magnetic field probed at two spatial scales are analyzed for the entire protostellar cluster sample and for a subset of objects in NGC 6334." (abstract)
- Target **NGC 6334 (I, In, IV, V, IR)**: coordinates NGC6334I 17:20:53.41 -35:46:57.8 (J2000)  
  > "NGC6334I & 17:20:53.41 & -35:46:57.8 & -8 & 1.3" (Table 2); z/distance 1.3 kpc  
  > "NGC6334I & 17:20:53.41 & -35:46:57.8 & -8 & 1.3" (Table 2); distance from _not stated_
- Target **G14.225-0.506 (G14)**: coordinates G14S (1) 18:18:13.80 -16:57:11.5  
  > "G14S (1) & 18:18:13.80 & -16:57:11.5 & 20 & 2.3" (Table 2); z/distance 2.3 kpc  
  > "G14S (1) & 18:18:13.80 & -16:57:11.5 & 20 & 2.3" (Table 2); distance from _not stated_
- Target **G35.2N**: coordinates 18:58:12.72 +01:40:42.7  
  > "G35.2N is associated with a massive star forming region at a distance of 2.19 kpc" (G35.2N description); z/distance 2.19 kpc  
  > "G35.2N is associated with a massive star forming region at a distance of 2.19 kpc" (G35.2N description); distance from cite: dent1989; sanchez2013d  
  > "G35.2N is associated with a massive star forming region at a distance of 2.19 kpc" (G35.2N description)
- Target **IRAS 18360-0537 (I18360)**: coordinates 18:38:40.73 -05:35:04.0  
  > "at a distance of 6.3 kpc (cite: xu_J_2021)" (I18360 description); z/distance 6.3 kpc  
  > "at a distance of 6.3 kpc (cite: xu_J_2021)" (I18360 description); distance from cite: xu_J_2021  
  > "at a distance of 6.3 kpc (cite: xu_J_2021)" (I18360 description)
- Target **G28.34+0.06 (MM4, MM9)**: coordinates MM4 (1) 18:42:51.05 -04:03:08.6  
  > "G28-MM4 (1) & 18:42:51.05 & -04:03:08.6 & 78.0 & 4.8" (Table 2); z/distance 4.8 kpc  
  > "G28-MM4 (1) & 18:42:51.05 & -04:03:08.6 & 78.0 & 4.8" (Table 2); distance from _not stated_
- Target **G34.43+0.24**: coordinates 18:53:18.01 +01:25:25.6  
  > "G34.43 (1) & 18:53:18.01 & 01:25:25.6 & 57 & 1.57" (Table 2); z/distance 1.57 kpc  
  > "G34.43 (1) & 18:53:18.01 & 01:25:25.6 & 57 & 1.57" (Table 2); distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00793.S
- bands: _not stated_
- frequencies and spectral setup: Three 1.875 GHz windows at 216.44, 218.54, 233.55 GHz, 1920 channels each; three narrow 58.6 MHz windows  
  > "The correlator was configured to cover three 1.875 GHz spectral windows centered at sky frequencies of 216.44, 218.54 and 233.55 GHz, respectively." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA main array, C43-1 and C43-4  
  > "we adopted array configurations of C43-1 and C43-4" (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1" (C43-1) and 0.4" (C43-4)  
  > "at resolutions of 1$^{\prime\prime}$ and 0$^{\prime\prime}$.4" (abstract)
- max recoverable scale: _not stated_
- sensitivity: 1 sigma rms 30 to 70 uJy in Stokes Q and U  
  > "With a $1 \sigma$ rms sensitivity of 30 to 70 $\mu$Jy in Stokes $Q$ and $U$ images" (3.1)
- time on source: _not stated_
- observing dates: 2018 (Mar-Nov), see Table 1  
  > "Observations of 17 high-mass protocluster forming clumps were conducted during 2018 in full polarization mode" (2 Observations)
- pi or archival as stated: PI Qizhou Zhang  
  > "under project 2017.1.00793.S (PI Qizhou Zhang)" (2 Observations)
- External data: Gas temperatures (~100 K, >300 K locally) from CH3OH in NGC 6334, used as dust temperature  
  > "The dust temperature is approximated by the gas temperature reported in (cite: liu_J2023a)" (4.1) [from (cite: liu_J2023a)]
- External data: Dust emissivity index beta=1.5  
  > "a dust emissivity spectral index $\beta$ of 1.5 (cite: beuther2007b)" (4.1) [from (cite: beuther2007b)]

## Processing

### Calibration

- pipeline or manual: Initially calibrated by the ALMA North American ARC using CASA  
  > "The visibility measurement sets were initially calibrated by the ALMA North American ARC using the Common Astronomy Software Applications package (CASA)" (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Phase-only self-cal on Stokes I continuum, two to three iterations, applied to Stokes I only  
  > "Self-calibration steps involve visibility phases in two to three interactions." (2 Observations)

### Imaging

- task: CASA tclean  
  > "ran the ‘tclean’ task using Briggs weighting of the visibilities with a robust parameter of 0.5" (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "ran the ‘tclean’ task using Briggs weighting of the visibilities with a robust parameter of 0.5" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: default multiscale parameters  
  > "The default multiscale parameters were used during deconvolution." (2 Observations)
- continuum subtraction: Continuum built by averaging line-free channels  
  > "We averaged the line-free channels in the three 1.875 GHz spectral windows to construct the continuum emission" (2 Observations)
- line free channels: _not stated_
- primary beam correction: Not applied for magnetic field maps  
  > "images are not corrected by the primary beam of the telescope" (3.1)
- array combination: C43-1 and C43-4 combined; C43-4 restricted to baselines >250 m for RO analysis  
  > "visibilities from the configuration C43-4 after excluding baselines shorter than 250 m to avoid overlap with the C43-1 data" (3.2)
- smoothing: Images convolved to 3360 au and 760 au beams for the two datasets  
  > "We convovled images to a Gaussian beam of a FWHM angular size equivalent to 3360 au, and 760 au for the two data sets, respectively." (3.2)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Gravity force map method and temperature/column density of NGC 6334  
  > "we also derive ROs between magnetic field orientations and plane-of-the-sky gravitational forces (cite: liu_J2023a)" (4.1) [from (cite: liu_J2023a)]
- Dust opacity law kappa=(nu/THz)^beta  
  > "using the dust opacity law $\kappa = ({\nu \over THz})^\beta$ (cite: hildebrand1983)" (4.1) [from (cite: hildebrand1983)]
- Projected Rayleigh statistic  
  > "we analyze ROs of magnetic fields in NGC 6334 using the projected Rayleigh statistic (cite: jow2018)" (4.1) [from (cite: jow2018)]

### Not stated but needed to reproduce (our reading)

- Number of self-calibration iterations/solints per target and which targets were self-calibrated
- Line-free channel selection
- Image sizes, cell sizes, clean thresholds and masks
- CASA version
- Flux calibration accuracy
- Pixel sampling details and beams used for RO maps for each source
- Exact mosaicking procedure
- Whether the K-S comparison random distribution was simulated or analytic
- Column density map construction details (gas-to-dust ratio, mean molecular weight)

## Analysis recipe

1. **Calibrate and image continuum Stokes I, Q, U**: Calibration by ARC, phase self-cal on Stokes I, tclean of line-free continuum  
  > "The fully calibrated visibilities were then imaged in CASA." (2 Observations)
   - software: CASA
   - parameter: Briggs robust 0.5  
  > "Briggs weighting of the visibilities with a robust parameter of 0.5" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive magnetic field position angles**: theta = 0.5 arctan(U/Q), 3 sigma cutoff on Q and U, rotate by 90 deg  
  > "The PAs of the magnetic field follow by rotating the electric field by $90^\circ$." (3.1)
   - parameter: 3 sigma cutoff  
  > "Applying a threshold cutoff of 3$\sigma$, the rms of the noise level, to the Stokes $Q$ and $U$ emission" (3.1)
   - fitting: _not stated_
   - validation: PA uncertainty 28.65 deg sigma_p/I_p  
  > "the $1 \sigma$ uncertainty in PA is given by $28.65^\circ \frac{\sigma_p}{I_p}$" (3.1)
3. **Relative orientation between scales**: Compare PA from C43-1 and C43-4 (>250 m), absolute differences folded to 0-90 deg; sources convolved to common linear resolution; G28 and I18360 excluded; K-S test vs random 3D angles  
  > "we took the absolute values of the relative orientations and limited the relative angles from $0^\circ$ to $90^\circ$" (3.2)
   - parameter: Sampling at 0.5 of the C43-4-restricted beam  
  > "The magnetic field data are sampled at 0.5 of the synthesized beam of the C43-4-restricted data" (3.2)
   - fitting: K-S test against random angles in 3D  
  > "A Kolmogorov-Smirnov (K-S) test is performed" (3.2)
   - validation: _not stated_
4. **Column density map and projected Rayleigh statistic vs density**: 1.3 mm continuum to N_H with kappa=1 cm2/g at 230 GHz, beta=1.5, T from CH3OH; normalized PRS (alignment measure) vs column density; RO with local gravity  
  > "We converted the 1.3-mm continuum emission to column densities, using the dust opacity law $\kappa =  ({\nu \over THz})^\beta$ (cite: hildebrand1983) and a dust emissivity spectral index $\beta$ of 1.5" (Discussions, RO dependence on densities)
   - assumption: beta=1.5; dust opacity 1 cm2/g at 230 GHz; dust temperature = gas temperature (~100 K)  
  > "This formulation results in a dust opacity of 1 $cm^2~g^{-1}$ at 230 GHz" (4.1)
   - fitting: _not stated_
   - validation: Comparison of RO with local gravity direction  
  > "the magnetic field is mostly parallel to the direction of the inferred gravitational force" (4.1)

## Software

- **CASA** : Calibration and imaging (tclean)  
  > "The fully calibrated visibilities were then imaged in CASA." (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| K-S probability, entire sample RO vs random | 6e-6 | not stated | dimensionless | 3 | We find a probability of $6 \times 10^{-6}$ that the two are drawn from the same population. |
| K-S probability, NGC 6334 combined | 2e-9 | not stated | dimensionless | 3 | We find a probability of $2 \times 10^{-9}$ that the two are drawn from the same population. |
| K-S probability for NGC 6334 I, In, IV, V | 0.07, 0.002, 6e-5, 0.4 | not stated | dimensionless | 3 | 0.07, 0.002, $6 \times 10^{-5}$, and 0.4 for NGC 6334 I, In, IV and V, respectively |
| K-S probability, G14 | 0.6 | not stated | dimensionless | 3 | We found a probability of 0.6 that the two are drawn from the same population. |

## Qualitative findings

- Parallel alignment excess at N_H > 1e23 cm^-2 and aligned with gravity direction in NGC 6334  
  > "at column densities greater than $10^{23}$ cm$^{-2}$, the magnetic field is mostly parallel to the $N_{{\rm H}_{2}}$ structures and the direction of local gravity" (4.1)

## Claim tuples

- H: Magnetic field orientations at envelope scale are correlated with those at core scale | E: RO between C43-1 and C43-4-restricted PA, K-S test vs random | R: Bimodal ROs peaking at 0 and 90 deg; K-S p=6e-6 (all), 2e-9 (NGC 6334) | F: Envelope-scale fields are aligned with or orthogonal to core fields | **supported**
- H: Gravitational collapse causes the parallel ROs at high density | E: Normalized PRS vs column density and RO with local gravity in NGC 6334 | R: Parallel excess above 1e23 cm^-2; field parallel to gravity from 5e22 to 2e24 | F: Gravity drags and reorients the field | **supported**

## Reasoning

- Why this data: Follow-up of SMA study at higher resolution to probe 10^3 au envelope scales  
  > "The goal of this ALMA study is to image the magnetic field at protostellar envelope scale of $10^3$ au." (1 Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): G14 RO distribution cannot be distinguished from random due to small numbers; G28 and I18360 excluded  
  > "the hypothesis that the RO distribution in G14 is randomly distributed cannot be ruled out due to small number statistics" (3.2)
- Caveat (inferred, ours): PRS and gravity analysis only for NGC 6334
- Caveat (inferred, ours): Independent samples reduced by factor ~4 relative to pixel counts, K-S p-values may be overstated
- Caveat (inferred, ours): Dust temperature assumed equal to gas temperature; no uncertainty propagation
- Caveat (inferred, ours): Gravity from plane-of-sky column density only

## Reproducibility

- Data public (paper): ALMA project 2017.1.00793.S acknowledged; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2017.1.00793.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: Full self-cal parameters
- Missing: Column density map recipe details
- Missing: Code for RO/PRS/K-S
- Data volume (inferred): Several hundred GB to ~1 TB raw for 12 execution blocks, 34 pointings
- Score (inferred): 6/5, Project code, robust, baseline cut and equations given; but versions, self-cal, mask and map details missing.
- Rediscovery candidate: yes, Archival data, numeric K-S probabilities, reasonably complete recipe, though some settings unstated.

## Links

- Method: (cite: jow2018) (Projected Rayleigh statistic)
- Method: (cite: zhang2014) (RO method precedent)
- Companion: (cite: liu_J2023a) (Detailed NGC 6334 analysis, temperatures and gravity)
- Companion: (cite: liu_J2020) (G28 analysis)
- Related: SMA polarization survey (Zhang et al. 2014)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 51,
  "rate": 0.622
 },
 "evidence_ok": true
}
```
