# Planetary System Formation in the Protoplanetary Disk around HL Tauri

`2016ApJ...818..158A` | The Astrophysical Journal 2016 | first author: Akiyama, Eiji | arXiv: 1511.04822 | DOI: 10.3847/0004-637X/818/2/158

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: If the HL Tau disk gaps are opened by unseen forming bodies, what are their masses, how might they have formed (GI) and how did they reach their current locations (type II migration)?  
  > "Assuming that the observed gaps are opened up by currently forming, unseen bodies, we estimate the mass of such hypothetical bodies" (abstract)
- Target **HL Tau**: coordinates _not stated_; z/distance approximately 140 pc  
  > "because of its nearness to the Sun with a distance of approximately 140 pc (cite: elias78; kenyon94)" (Introduction); distance from (cite: elias78; kenyon94)  
  > "because of its nearness to the Sun with a distance of approximately 140 pc (cite: elias78; kenyon94)" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00015.SV
- bands: Band 3, 6, 7 (2.9, 1.3, 0.87 mm)  
  > "observed on October 24th 2014 at band 3, 6, 7, corresponding to 2.9, 1.3, and 0.87 mm in wavelength" (Observation and Data Reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12 m array, 28-37 antennas  
  > "The number of antennas used in the 12 m array was between 28 and 37." (Observation and Data Reduction)
- configurations: _not stated_
- baselines: ~15 to ~15238 m  
  > "The baseline lengths were between $\sim$ 15 and $\sim$ 15238 m" (Observation and Data Reduction)
- angular resolution: 0.0822x0.0544'' (B3), 0.0346x0.0225'' (B6), 0.0189x0.0285'' (B7)  
  > "providing a synthesized beam of 0.0822$''$ $\times$ 0.0544$''$ at band 3, 0.0346$''$ $\times$ 0.0225$''$ at band 6, and 0.0189$''$ $\times$ 0.0285$''$ at band 7" (Observation and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 7.2 h (B3), 4.9 h (B6), 5.4 h (B7)  
  > "the corresponding integration time on source for each band after data reduction is 7.2 h, 4.9 h, and 5.4 h, respectively" (Observation and Data Reduction)
- observing dates: October 24th 2014  
  > "observed on October 24th 2014 at band 3, 6, 7" (Observation and Data Reduction)
- pi or archival as stated: _not stated_
- Other facility **CARMA**: 1.3 mm flux density 700 ± 10.3 mJy used for consistency check  
  > "flux density of 700 $\pm$ 10.3 mJy that is derived from the previous observations at $\lambda = 1.3$ mm taken by the Combined Array for Research in Millimeterwave Astronomy (cite: kwon11)" (Results)
- External data: Best-fit disk model parameters (p, q, beta, kappa0, r_in, r_c, gas-to-dust, M_disk, inclination) and M*=0.55 Msun  
  > "We simply use the results of their best fit case (see Table [\[table1\]](#table1))." (Disk model) [from (cite: kwon11)]
- External data: Gap-depth planet mass formula and disk parameters  
  > "Here, we follow a method derived by (cite: kanagawa15)." (The mass of hypothetical bodies) [from (cite: kanagawa15)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.2.2  
  > "Data reduction was performed using version 4.2.2 of the Common Astronomy Software Applications package (CASA)" (Observation and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Phase-only, 4 steps, solint 600s, 300s, 150s, scan time; minblperant=4, minsnr=2  
  > "The self-calibration was conducted in four steps by decreasing the solution interval from 600 sec, 300 sec, 150 sec, and finally to scan time." (Observation and Data Reduction); "We applied minblperant = 4 and minsnr = 2 for the self calibration" (Observation and Data Reduction)

### Imaging

- task: CLEAN  
  > "the deconvolution was done using task CLEAN to make images from the final calibrated visibilities" (Observation and Data Reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Start with central Gaussian-like component, gradually extend CLEAN box, finally clean all  
  > "Then, we extended the CLEAN box area gradually, and finally we CLEANed all of the components." (Observation and Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 10, 18, 24 uJy (B3, B6, B7)  
  > "the corresponding achieved rms are down to 10, 18, and 24 $\mu$Jy, respectively" (Results)

### Inherited from earlier work

- Gap profile taken along position angle 138 deg  
  > "along the direction of position angle of 138$\ensuremath{^\circ}$ (cite: partnership)" (Results) [from (cite: partnership)]
- Disk model and temperature power laws  
  > "We adopt a simplified version of a disk model used in (cite: kwon11)" (Disk model) [from (cite: kwon11)]

### Not stated but needed to reproduce (our reading)

- CLEAN weighting/robust, cell size, image size, deconvolver, threshold
- Which spectral windows/channels used for continuum
- Flux scale and which calibrator fixed it
- Disk T0, alpha, aspect ratio h_p values used for Kanagawa mass
- Table 3 temperature normalization T_i0
- Inclination used to deproject radial profile
- Crida-method results not shown

## Analysis recipe

1. **Re-process SV data**: Self-calibration with relaxed flagging, then incremental CLEAN  
  > "we increase the quantity of contributing data by modifying, for example, the minimum number of baselines per antenna (minblperant) and the minimum signal to noise ratio (minsnr)" (Observation and Data Reduction)
   - software: CASA
   - parameter: minblperant=4, minsnr=2  
  > "We applied minblperant = 4 and minsnr = 2 for the self calibration" (Observation and Data Reduction)
   - fitting: _not stated_
   - validation: Compared to archive image and CARMA flux  
  > "Figure [2](#fig:fig2) shows the comparison between our re-processed 0.87 mm continuum image (a) and the original ALMA archive image (b)." (Results)
2. **Measure gap positions and widths**: Minimum of radial surface brightness; width at L_gap+0.5 ΔL_gap  
  > "we find out the positions at which the surface brightness takes the value of $L_{gap} + 0.5 \Delta L_{gap}$" (Results)
   - assumption: Star at the continuum peak  
  > "it is assumed that the central star is located at the observed continuum peak" (The mass of hypothetical bodies)
   - fitting: _not stated_
   - validation: _not stated_
3. **Planet masses**: Hill radius analysis from gap width; Kanagawa et al. gap-depth formula  
  > "We estimate their masses by following two approaches; the Hill radius analysis and a more detailed method in which the balance of angular momentum transfer is considered." (The mass of hypothetical bodies)
   - assumption: M*=0.55 Msun; Kwon11 disk model  
  > "where $M_* = 0.55 M_{\odot}$ is the stellar mass (cite: kwon11)" (The mass of hypothetical bodies)
   - fitting: _not stated_
   - validation: Consistent with Crida06 method (not shown)  
  > "within the uncertainty of disk viscosity and stellar mass, the resultant values are all consistent with those summarized in Table [1](#table2)" (The mass of hypothetical bodies)
4. **GI and migration tests**: Toomre Q minimum surface density and cooling minimum temperature (Rafikov05); gap-opening mass and Crida06 criterion for type II migration  
  > "Based on the so-called Toomre Q condition (cite: toomre64), $\Sigma_{g,min}$ can be written as (cite: rafikov05)" (Formation Mechanisms)
   - assumption: kappa0=0.01 cm2/g, nu0=230 GHz, beta=0.729  
  > "We set $\kappa_0 =0.01$ cm$^2$ g$^{-1}$, $\nu_0=230$ GHz and $\beta=0.729$" (Formation Mechanisms)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.2: Calibration, self-calibration and CLEAN imaging  
  > "Data reduction was performed using version 4.2.2 of the Common Astronomy Software Applications package (CASA)" (Observation and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Gap radii | 13.5, 32.4, 65.2, 77.2 | +0.4/-0.4, +0.6/-0.4, +1.3/-0.9, +0.8/-0.7 | AU | 2 | / 1 / 13.5 $^{+0.4}_{-0.4}$ / 5.0 $^{+0.1}_{-0.1}$ / 88.8 $^{+5}_{-5}$ / 0.85 / |
| Gap widths | 5.0, 4.1, 6.2, 4.5 | ~0.1-0.8 | AU | 2 | we obtain the following gap widths; 5.0, 4.1, 6.2, and 4.5 AU |
| Total flux densities | 73 mJy (B3), 800 mJy (B6), 2.3 Jy (B7) | not stated | mJy/Jy | 1 | The total flux densities at each band are measured to be 73 mJy in band 3, 800 mJy in band 6, and 2.3 Jy in band 7 |
| Kanagawa planet masses | 0.85, 0.61, 0.62, 0.51 | not stated | M_J | 3 | / 2 / 32.4 $^{+0.6}_{-0.4}$ / 4.1 $^{+0.2}_{-0.2}$ / 3.6 $^{+0.7}_{-0.6}$ / 0.61 / |
| Hill masses | 88.8, 3.6, 1.5, 0.3 | ±5, +0.7/-0.6, ±0.5, ±0.1 | M_J | 3 | / 4 / 77.2 $^{+0.8}_{-0.7}$ / 4.5 $^{+0.4}_{-0.4}$ / 0.3 $^{+0.1}_{-0.1}$ / 0.51 / |
| Merged gap 3+4 Hill mass | 22 | ±3 | M_J | 3 | which ends up with M$_{p,hill}$ that becomes $22\pm{3}$ $M_J$ |
| Long-baseline coefficient a | 1.6 | not stated | dimensionless | 1 | For our re-processed images, $a$ becomes 1.6 |

## Qualitative findings

- GI can operate beyond ~52 AU; bodies can undergo inward type II migration  
  > "GIs can occur in the region beyond $r \sim$ 52 AU, where both of the conditions are simultaneously met." (Formation Mechanisms)

## Claim tuples

- H: Gaps are opened by planets of what mass? | E: Hill radius and Kanagawa gap-depth analyses | R: Kanagawa masses 0.5-0.85 MJ; Hill gives 88.8 MJ for innermost gap | F: Masses comparable to or less than Jupiter; Hill method overestimates | **supported**
- H: GI can form the bodies in the outer disk | E: Toomre Q and cooling criteria | R: Both satisfied at 65.2 and 77.2 AU | F: GI is likely for outer gaps | **supported**
- H: Inner gaps arise from migrated bodies | E: Gap-opening mass and Crida criterion | R: Type II migration likely for all bodies | F: Conjecture: GI formation plus inward migration | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Re-process to improve images for more accurate mass estimates  
  > "we re-process the ALMA archive data because a better quality of the dust continuum maps is desired" (Introduction)
- Alternative: Hill radius method judged over-simplified  
  > "This may suggest that the method itself is over-simplified, and hence leads to a significant overestimate of planetary masses." (The mass of hypothetical bodies)
- How they decided it was enough: _not stated_
- Limitation (authors): Only 17 of 780 baselines exceed 10 km; images could be improved  
  > "only 17 out of 780 antenna combinations had a baseline of more than 10 km" (Results)
- Caveat (inferred, ours): Imaging parameters missing; gap properties depend on reprocessing
- Caveat (inferred, ours): Low-mass planet masses depend on assumed alpha and aspect ratio
- Caveat (inferred, ours): Dust continuum used with a gas disk model from lower-resolution data
- Caveat (inferred, ours): Relaxed minsnr/minblperant flagging may bias the image

## Reproducibility

- Data public (paper): Public in ALMA science verification archive  
  > "All of the data including observed raw visibility data, calibrated data set, and images are available in the ALMA science verification data archive." (Observation and Data Reduction)
- Products in archive: _not stated_
- Missing: CLEAN parameters
- Missing: disk temperature normalization and alpha/h_p
- Missing: Crida results
- Data volume (inferred): ~100-300 GB
- Score (inferred): 3/5, Public data and numbers, but imaging parameters and model inputs missing.
- Rediscovery candidate: no, Imaging recipe incomplete and mass estimates depend on unstated parameters.

## Links

- Method: (cite: kanagawa15) (Gap-depth planet mass formula)
- Method: (cite: kwon11) (Disk model)
- Companion: (cite: partnership) (ALMA SV campaign HL Tau results)
- Related: ALMA long-baseline science verification campaign

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
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
  "facts": 68,
  "stated": 35,
  "rate": 0.515
 },
 "evidence_ok": true
}
```
