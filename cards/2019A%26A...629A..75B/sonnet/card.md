# First detections of H<SUP>13</SUP>CO<SUP>+</SUP> and HC<SUP>15</SUP>N in the disk around HD 97048. Evidence for a cold gas reservoir in the outer disk

`2019A&A...629A..75B` | Astronomy and Astrophysics 2019 | first author: Booth, Alice S. | arXiv: 1907.08060 | DOI: 10.1051/0004-6361/201834388

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Can chemistry alone explain the radial emission profiles of HCO+, H13CO+ and HC15N in the HD 97048 disk, or are modifications to the underlying gas structure required?  
  > "The aim of this work is to investigate whether or not chemistry alone can explain the radial emission profiles of these molecules, or if modifications to the underlying disk gas structure are required." (Introduction)
- Target **HD 97048**: coordinates 11:08:03.2, -77:39:17  
  > "located in the Chameleon I star-forming region at 11:08:03.2, -77:39:17 at a distance of $184^{+2}_{-2}$ pc (cite: 2018A&A...620A.128V)" (2 The source: HD 97048); z/distance 184 (+2/-2) pc  
  > "located in the Chameleon I star-forming region at 11:08:03.2, -77:39:17 at a distance of $184^{+2}_{-2}$ pc (cite: 2018A&A...620A.128V)" (2 The source: HD 97048); distance from Vioque et al. 2018 (Gaia DR2-based)  
  > "located in the Chameleon I star-forming region at 11:08:03.2, -77:39:17 at a distance of $184^{+2}_{-2}$ pc (cite: 2018A&A...620A.128V)" (2 The source: HD 97048)

## Data provenance

- ALMA projects: 2011.0.00863.S, 2013.1.00658.S, 2012.1.00031.S
- bands: _not stated_
- frequencies and spectral setup: Cycle 2: four spectral windows, two continuum, two centred on J=3-2 and J=4-3 lines; native resolution 0.21 km/s (Cycle 0)  
  > "This dataset consists of four spectral windows, two of which were tuned for continuum observations and two of which were centred on the $J=3-2$ and $J=4-3$ spectral lines." (3.1 Data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Cycle 0: 15.1-402 m; Cycle 2: 21.4-555.5 m  
  > "Baselines (m) | 15.1 - 402 | | 21.4 - 555.5" (Table 1)
- angular resolution: Cycle 0 beam 0.74'' x 0.51'' (natural weighting)  
  > "Synthesised beam | 0.74$''$ $\times$ 0.51$''$" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: rms 0.016 Jy/beam per channel at 0.21 km/s (Cycle 0)  
  > "$\sigma$ (Jy beam$^{-1}$ per channel$^{a}$) | 0.016 | 0.016 | 0.016" (Table 1)
- time on source: Cycle 0: 23 min 59 s; Cycle 2: 7 min 10 s  
  > "On source integration time (min,sec) | 23,59 | | 7,10" (Table 1)
- observing dates: Cycle 0: 14 December 2012; Cycle 2: 22 May 2015  
  > "Date observed | 14 December 2012 | | 22 May 2015" (Table 1)
- pi or archival as stated: _not stated_
- Line: HCO+ J=4-3 (346.998 GHz)
- Line: H13CO+ J=4-3 (346.998 GHz)
- Line: HC15N J=4-3 (344.200 GHz)
- Line: CO J=3-2 (345.796 GHz)
- External data: mm-dust continuum radial profile (super-uniform weighting; uv-modelled profile)  
  > "Also plotted is the mm-dust radial profile from (cite: 2016ApJ...831..200W) where the image was generated using super-uniform weighting in CLEAN." (4.2 Deprojection and azimuthal averaging) [from (cite: 2016ApJ...831..200W)]
- External data: HD 97048 disk structure (gas density, temperature, ionisation) from DIANA  
  > "we use the publicly available HD 97048 disk structure from the DIscANAlysis project (DIANA)" (5 Chemical Modelling) [from (cite: 2016A&A...586A.103W; 2017A&A...607A..41K; 2019PASP..131f4301W)]
- External data: Reaction rate coefficients  
  > "The reaction rate coefficients, $k_i$, are given in Table [\[table3\]](#table3), where $i$ is the number of the reaction as compiled by (cite: 2015ApJ...807..120A)." (5 Chemical Modelling) [from (cite: 2015ApJ...807..120A)]
- Simulation/model as data: LIME radiative transfer models on DIANA disk structure with analytic HCO+ abundance  
  > "Synthetic channel maps were generated using LIME version 1.6 (cite: 2010A&A...523A..25B)" (5 Chemical Modelling)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.6.0  
  > "These latter data were self-calibrated using CASA (version 4.6.0)." (3.1 Data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Cycle 0: self-calibrated measurement sets from earlier work; Cycle 2 raw data self-calibrated with continuum windows after flagging line channels  
  > "The two broadband continuum windows were self-calibrated after flagging the line containing channels and then used to self-calibrate the respective higher spectral resolution $J=3-2$ and $J=4-3$ line containing spectral windows." (3.1 Data reduction)

### Imaging

- task: CASA CLEAN  
  > "The lines listed in Table [\[table1\]](#table1) were imaged in CASA using CLEAN with natural weighting and using a Keplerian mask" (3.2 Molecular line imaging)
- deconvolver: _not stated_
- weighting robust: natural  
  > "CLEAN image weighting | natural" (Table 1)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian mask from 1 to 800 au, local linewidth 1 km/s at 100 au  
  > "The Keplerian mask was set to encompass emission from 1 au to 800 au using an estimated local linewidth of 1 km s$^{-1}$ at 100 au." (3.2 Molecular line imaging)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub; checked against image-plane baseline subtraction  
  > "subtracted the continuum emission from the two line containing spectral windows using the CASA task, `uvcontsub`." (3.1 Data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: imsmooth to common beam 0.7'' x 0.6'', PA -26 for HCO+/H13CO+ ratio  
  > "The new beam is 0.7$''$ $\times$ 0.6$''$ with a position angle of -26." (4.2 Deprojection and azimuthal averaging)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Continuum and CO line data previously presented; self-calibrated phase-corrected continuum-subtracted Cycle 0 sets taken from earlier work  
  > "see (cite: 2016ApJ...831..200W) and (cite: 2017A&A...597A..32V) for full details" (3.1 Data reduction) [from (cite: 2016ApJ...831..200W); (cite: 2017A&A...597A..32V)]
- HCO+ abundance parametrisation  
  > "Following (cite: 2015ApJ...807..120A), we analytically derive the abundance" (5 Chemical Modelling) [from (cite: 2015ApJ...807..120A)]
- CO abundance parameterisation  
  > "We parameterise the abundance distribution as described by (cite: 2014ApJ...788...59W)." (5 Chemical Modelling) [from (cite: 2014ApJ...788...59W)]

### Not stated but needed to reproduce (our reading)

- Cycle 0 calibration details and flux calibrator
- Number of clean iterations and thresholds, cell and image size
- Line-free channels used for rms and continuum
- Exact Keplerian mask parameters (stellar mass, inclination used)
- Self-calibration solution intervals
- Role of project 2012.1.00031.S
- Exact LIME settings (photons, grid, turbulence)
- HC15N rest-frame velocity and line profile extraction ellipse parameters

## Analysis recipe

1. **Calibrate and continuum-subtract**: Self-calibrate with continuum windows, then uvcontsub; check against line-profile baseline subtraction  
  > "we checked that continuum subtraction in the $uv$ domain did not over-subtract the or emission" (3.1 Data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: Line profiles agree within 1 sigma between both methods  
  > "the line profiles for both species (CO and ) using both methods agree to within $1\sigma$" (3.1 Data reduction)
2. **Image lines and make moment maps**: CLEAN with natural weighting and Keplerian mask; moment 0 with mask, moment 1 with 3 sigma clip  
  > "The moment 0 maps were made using a Keplerian mask and the moment 1 maps were made using a 3$\sigma$ clip." (4.1 Channel maps, moment maps, and line profiles)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Deproject and azimuthally average**: Radial bins of 0.3'' on deprojected moment 0 maps; errors = std/sqrt(beams per annulus)  
  > "The bin size chosen was 0.3$''$ because this is two times the pixel size of the images and is approximately half of the beam size." (4.2 Deprojection and azimuthal averaging)
   - assumption: Inclination 41 deg, PA 3 deg, stellar mass 2.5 Msun, azimuthal symmetry  
  > "seen with an inclination angle of $41 \degree$ and a position angle of $3 \degree$" (2 The source: HD 97048)
   - fitting: _not stated_
   - validation: Consistent with profiles from unclipped, unmasked maps  
  > "The recovered fluxes and trends in the resulting radial profiles are consistent with radial profiles generated from un-clipped and un-masked integrated intensity maps." (4.2 Deprojection and azimuthal averaging)
4. **HCO+/H13CO+ intensity ratio**: Smooth cubes to a common beam with imsmooth, remake moment maps, divide radial profiles  
  > "the channel maps have been smoothed to the same beam size using the CASA task, `imsmooth`." (4.2 Deprojection and azimuthal averaging)
   - software: CASA
   - fitting: _not stated_
   - validation: uvtaper imaging gave consistent results  
  > "found that the results were consistent with using `imsmooth`" (4.2 Deprojection and azimuthal averaging)
5. **Chemical + radiative transfer modelling**: Analytic steady-state HCO+ abundance on DIANA structure; LIME LTE cubes smoothed to observed beam; by-eye comparison of radial profiles over Models 1-5 varying abundance multipliers and cavity gas  
  > "We run a range of models step-by-step altering the initial model to find a best by-eye fit to the observed radial profiles." (5 Chemical Modelling)
   - software: LIME, CASA
   - parameter: kappa_HCO+ = 0.2; cavity gas eta = 0.2; kappa_H13CO+ = 2 (<200 au), 6 (>200 au)  
  > "The best by-eye fit for $\kappa_{\ce{H^{13}CO^{+}}}$ was found to be 6 relative to the abundances in Model 2" (5.2 Modifications to the Fiducial Model)
   - assumption: HCO+/H13CO+ = 12C/13C = 69; CO/H = 1.4e-4 above 20 K; gas-to-dust 100; LTE  
  > "The abundance is determined by simply assuming that /=/ = 69 (cite: 1999RPPh...62..143W)." (5 Chemical Modelling)
   - fitting: By-eye, no formal fit  
  > "find a best by-eye fit to the observed radial profiles" (5 Chemical Modelling)
   - validation: Dust opacity check changed profiles by 10-20%; critical density check supports LTE  
  > "The resulting radial profiles differed by 10 to 20% only from the models where we neglect dust opacity" (5.2 Modifications to the Fiducial Model)

## Software

- **CASA** 4.6.0: Self-calibration, uvcontsub, CLEAN imaging, imsmooth, imcontsub  
  > "These latter data were self-calibrated using CASA (version 4.6.0)." (3.1 Data reduction)
- **LIME** 1.6: Synthetic channel maps from disk models  
  > "Synthetic channel maps were generated using LIME version 1.6" (5 Chemical Modelling)
- **makemask.py** : Keplerian mask for imaging  
  > "Publicly available on GitHub at <https://github.com/kevin-flaherty/ALMA-Disk-Code/blob/master/makemask.py>" (3.2 Molecular line imaging)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HCO+/H13CO+ integrated intensity ratio (average) | 12 | 3 | dimensionless | 4 | has an average value of $12~\pm~3$ |
| Innermost radius of H13CO+ emission | 41 | 2 | au | 2 | emission is detected down to an average radial distance of $41\pm2$ au |
| Innermost radius of CO emission | 14 | 1 | au | 2 | corresponds to emission detected down to an average radial distance of $14\pm1$ au |
| Best-fit HCO+ abundance multiplier | 0.2 | not stated | dimensionless | 5 | of 0.2 relative to the abundance calculated using the analytical chemical model |
| HCO+/H13CO+ ratio in outer disk (>200 au), Model 5 | 11.5 | not stated | dimensionless | 5 | 11.5 (\> 200 au) |
| Gas surface density depletion in cavity | ~500 | not stated | dimensionless (factor) | 5 | then the gas surface density is $\approx$500 times less that in the dust cavity than in the inner edge of the outer disk |

## Qualitative findings

- HCO+ and H13CO+ show centrally peaked profiles with step-like changes in slope near the 2nd and 3rd dust rings; HC15N may follow the dust rings  
  > "The intensity profile appears to peak in a ring which appears to match well with the mm-sized dust distribution at the same spatial resolution." (6 Discussion)

## Claim tuples

- H: Does chemistry with a smooth disk structure explain the HCO+ and H13CO+ profiles? | E: LIME models on DIANA structure compared with observed radial profiles | R: Fiducial model overestimates emission and gives wrong morphology and ratio trend | F: Smooth model with canonical isotope ratio fails; gas in cavity and altered abundances needed | **supported**
- H: Is a constant HCO+/H13CO+ ratio consistent with the data? | E: Adjust H13CO+ abundance multiplier by region | R: Ratio needs to drop to ~35 inside 200 au and ~11.5 outside | F: Enhanced H13CO+ in the outer disk suggests a cold (<~10 K) reservoir; isotope-selective chemistry alone insufficient | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Dust opacity suppression of inner emission rejected (10-20% effect)  
  > "Hence, the emission in the inner disk is not significantly suppressed due to dust opacity." (5.2 Modifications to the Fiducial Model)
- How they decided it was enough: _not stated_
- Limitation (authors): Fits are by eye; no main-isotopologue HCN data; low S/N for HC15N  
  > "due to the low S/N of the data a centrally peaked smooth radial intensity profile cannot be ruled out" (4.2 Deprojection and azimuthal averaging)
- Caveat (inferred, ours): By-eye model fits with no uncertainties or degeneracy exploration
- Caveat (inferred, ours): Fractionation inference depends on uncertain DIANA gas temperatures
- Caveat (inferred, ours): Low resolution (~50 au) cannot resolve ring structure
- Caveat (inferred, ours): CO J=3-2 missing flux near systemic velocity

## Reproducibility

- Data public (paper): Archival Cycle 2 raw data; DIANA model public  
  > "the raw archival data from the Cycle 2 program 2013.1.00658.S" (3.1 Data reduction)
- Products in archive: _not stated_
- Code: Keplerian mask script on GitHub (not the authors' own models)  
  > "Publicly available on GitHub at <https://github.com/kevin-flaherty/ALMA-Disk-Code/blob/master/makemask.py>" (3.2 Molecular line imaging)
- Missing: Cycle 0 self-calibrated measurement sets (derived from earlier papers)
- Missing: LIME configuration
- Missing: Exact imaging parameters
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and clear model description, but key calibration and imaging parameters and by-eye fits limit exact reproduction.
- Rediscovery candidate: no, Main conclusions rely on by-eye model fits and inherited calibrated Cycle 0 data.

## Links

- Method: (cite: 2015ApJ...807..120A) (Analytic HCO+ abundance prescription)
- Method: (cite: 2017A&A...606A.125S) (Keplerian masking for improved moment maps)
- Companion: (cite: 2016ApJ...831..200W) (Original Cycle 0 ALMA data of HD 97048)
- Companion: (cite: 2017A&A...597A..32V) (Cycle 2 ALMA data of HD 97048)
- Related: DIANA

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 45,
  "rate": 0.6
 },
 "evidence_ok": true
}
```
