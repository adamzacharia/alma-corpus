# The Disk Substructures at High Angular Resolution Project (DSHARP). III. Spiral Structures in the Millimeter Continuum of the Elias 27, IM Lup, and WaOph 6 Disks

`2018ApJ...869L..43H` | The Astrophysical Journal Letters 2018 | first author: Huang, Jane | arXiv: 1812.04193 | DOI: 10.3847/2041-8213/aaf7a0

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: protoplanetary_disks
- Question: What are the morphology, orientation, pitch angles and contrasts of the millimeter continuum spiral arms in the Elias 27, IM Lup and WaOph 6 disks, and what could cause them?  
  > "We present an analysis of ALMA 1.25 millimeter continuum observations of spiral structures in three protoplanetary disks from the Disk Substructures at High Angular Resolution Project." (abstract)
- Target **Elias 27**: coordinates _not stated_; z/distance 116 (+19/-10) pc  
  > "Elias 27 is a 0.8 Myr M0 star located $116\substack{+19\\-10}$ pc away in the $\rho$ Oph star-forming region" (Source properties and observations); distance from Gaia (Gaia Collaboration 2018)  
  > "Elias 27 is a 0.8 Myr M0 star located $116\substack{+19\\-10}$ pc away in the $\rho$ Oph star-forming region" (Source properties and observations)
- Target **IM Lup**: coordinates _not stated_; z/distance 158±3 pc  
  > "IM Lup is a 0.5 Myr K5 star located $158\pm3$ pc away in the Lupus II cloud" (Source properties and observations); distance from Gaia (Gaia Collaboration 2018)  
  > "IM Lup is a 0.5 Myr K5 star located $158\pm3$ pc away in the Lupus II cloud" (Source properties and observations)
- Target **WaOph 6**: coordinates _not stated_; z/distance 123±2 pc  
  > "WaOph 6 is a 0.3 Myr K6 star located $123\pm2$ pc away in $\rho$ Oph." (Source properties and observations); distance from Gaia (Gaia Collaboration 2018)  
  > "WaOph 6 is a 0.3 Myr K6 star located $123\pm2$ pc away in $\rho$ Oph." (Source properties and observations)

## Data provenance

- ALMA projects: _none stated_
- bands: 1.25 mm continuum and 12CO J=2-1  
  > "The 1.25 mm continuum and $^{12}$CO $J=2-1$ emission of these three disks were observed as part of DSHARP." (Source properties and observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~40-60 mas (~6-7 au)  
  > "observed at a resolution of $\sim40-60$ mas ($\sim6-7$ au)" (abstract)
- max recoverable scale: Continuum MRS 11/1.4 arcsec (Elias 27), 11/3.4 (IM Lup), 10/1.4 (WaOph 6)  
  > "| Elias 27 continuum (fiducial) | 0, 0.06, 0.15, 0.3, 0.6 | 0.5 | $40 \times 20$ $(173)$ | $49 \times 47$ $(47)$ | 11, 1.4 | 4.8 | 0.014 |" (Table 1)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- External data: Disk inclinations and position angles used for deprojection (and disk dust radii, annular substructure nomenclature)  
  > "The inclinations and position angles used for deprojection are taken from (cite: 2018ApJ...869L..42H)" (2.1 Overview of spiral morphology) [from (cite: 2018ApJ...869L..42H)]
- External data: Gaia parallax distances  
  > "IM Lup is a 0.5 Myr K5 star located $158\pm3$ pc away in the Lupus II cloud (cite: alcala17; 2018AA...616A...1G)." (Source properties and observations) [from (cite: 2018AA...616A...1G)]
- External data: Continuum fluxes compared with single-dish measurements  
  > "the continuum flux measurements of these three disks from (cite: 2018ApJ...869L..41A) are consistent with single-dish measurements from (cite: 1994ApJ...420..837A) and (cite: 2007AA...461..983V)" (3.4 Spiral arm contrasts) [from (cite: 2018ApJ...869L..41A); (cite: 1994ApJ...420..837A); (cite: 2007AA...461..983V)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline, then phase and amplitude self-calibration  
  > "In brief, the data were first calibrated with the ALMA pipeline. We subsequently applied phase and amplitude self-calibration to each source" (Source properties and observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: multi-scale CLEAN  
  > "then used multi-scale `CLEAN` to image the continuum and $^{12}$CO." (Source properties and observations)
- deconvolver: _not stated_
- weighting robust: Briggs 0.5 (Elias 27 fid.), 1.0 (Elias 27 mid-res), 0.5 (IM Lup), 0 (WaOph 6)  
  > "| IM Lup continuum | 0, 0.03, 0.15, 0.45, 0.9, 1.35 | 0.5 | $33 \times 26$ (138) | $44\times 43$ (115) | 11, 3.4 | 7.1 | 0.014 |" (Table 1)
- uv taper: Elias 27 40x20 mas (173°); IM Lup 33x26 (138°); WaOph 6 55x10 (10°)  
  > "| WaOph 6 continuum | 0, 0.015, 0.06, 0.18, 0.36, 0.72 | 0 | $55\times 10$ (10) | $58\times54$ (84) | 10, 1.4 | 8.7 | 0.017 |" (Table 1)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: Elias 27: 0, 0.06, 0.15, 0.3, 0.6 arcsec; IM Lup: 0, 0.03, 0.15, 0.45, 0.9, 1.35; WaOph 6: 0, 0.015, 0.06, 0.18, 0.36, 0.72  
  > "| Elias 27 continuum (fiducial) | 0, 0.06, 0.15, 0.3, 0.6 | 0.5 | $40 \times 20$ $(173)$ | $49 \times 47$ $(47)$ | 11, 1.4 | 4.8 | 0.014 |" (Table 1)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Elias 27 49x47 mas; IM Lup 44x43; WaOph 6 58x54; Elias 27 mid-res 85x81  
  > "| WaOph 6 continuum | 0, 0.015, 0.06, 0.18, 0.36, 0.72 | 0 | $55\times 10$ (10) | $58\times54$ (84) | 10, 1.4 | 8.7 | 0.017 |" (Table 1)
- final rms: 0.014 (Elias 27, IM Lup), 0.017 (WaOph 6), 0.019 mJy/beam (Elias 27 mid-res)  
  > "| Elias 27 continuum (mid-res) | 0, 0.075, 0.15, 0.3, 0.4, 0.6 | 1.0 | $60 \times 40$ $(-6)$ | $85\times81$ $(-75)$ | 11, 1.4 | 9.4 | 0.019 |" (Table 1)

### Inherited from earlier work

- Observational setup, calibration, imaging and fiducial images taken from the DSHARP overview paper  
  > "Unless otherwise specified, the analysis in this work is based on the “fiducial” images from the overview paper." (Source properties and observations) [from (cite: 2018ApJ...869L..41A)]
- Disk geometry and annular substructure nomenclature  
  > "We use the same nomenclature to refer to these structures, e.g., D69 refers to a gap at a radius of 69 au" (2.1 Overview of spiral morphology) [from (cite: 2018ApJ...869L..42H)]
- Arm position finding approach (local maxima along rays)  
  > "This is similar to the approach used in (cite: 2016Sci...353.1519P)." (3.3 Spiral arm pitch angles) [from (cite: 2016Sci...353.1519P)]

### Not stated but needed to reproduce (our reading)

- Project codes and execution details of the underlying DSHARP data
- CASA version and self-calibration solution intervals
- Exact CLEAN threshold, masks, image size and cell size
- Line-free channels and continuum subtraction for 12CO
- Code for polar deprojection and local-maximum search (smoothing, peak criteria)
- Explicit selection of data points excluded as 'flattened' in arm fits

## Analysis recipe

1. **Deproject images and make non-axisymmetric residuals**: Deproject using literature inclination/PA, bin in 1 au annuli, subtract median radial profile  
  > "The axisymmetric profile is derived by deprojecting the disk, binning the pixels in au-wide annuli, and finding the median intensity in each bin." (2.1 Overview of spiral morphology)
   - parameter: Elias 27 PA 118.8°, inc 56.2°; IM Lup PA 144.5°, inc 47.5°; WaOph 6 PA 174.2°, inc 47.3°  
  > "the Elias 27 disk has a P.A. of 118$\ensuremath{^\circ}$8 and inclination of 56$\ensuremath{^\circ}$2" (2.1 Overview of spiral morphology)
   - fitting: _not stated_
   - validation: _not stated_
2. **Determine arm orientation (trailing/leading)**: Use 12CO J=2-1 channel maps, front/back side of flared emission and rotation direction  
  > "Thus, we can establish whether the spiral arms are trailing (the outer ends point opposite to the direction of disk rotation) or leading" (3.2 Orientation of the spiral arms)
   - fitting: _not stated_
   - validation: Consistent with earlier CO and scattered light orientations  
  > "The orientations we find are consistent with that derived for Elias 27 from $^{12}$CO emission in (cite: 2016Sci...353.1519P)" (3.2 Orientation of the spiral arms)
3. **Measure arm positions**: Local maxima along rays of fixed polar angle in deprojected residual maps; uncertainty from beam standard deviation scaled for deprojection  
  > "searching for local maxima along rays of fixed $\theta$." (3.3 Spiral arm pitch angles)
   - parameter: Elias 27: every 8° for R=50-110 au (fiducial), every 6° for R=110-230 au (mid-res); IM Lup: 15° for 25-75 au, 6° for 75-110 au; WaOph 6: 18° for 25-50 au, 9° for 50-80 au  
  > "The arm positions are measured every 18$^\circ$ between $R = 25-50$ au and then every 9$^\circ$ from $R=50-80$ au" (3.3 Spiral arm pitch angles)
   - fitting: _not stated_
   - validation: Positions checked against the other image and re-imaging with larger taper  
  > "We also re-imaged the other two disks with a larger taper to check that use of a slightly larger taper does not bias the measured positions" (3.3 Spiral arm pitch angles)
4. **Fit logarithmic and Archimedean spirals**: Each arm fit with R=R0 exp(b theta), pitch angle arctan|b|; Archimedean R=a+c theta  
  > "A logarithmic spiral takes the form $R(\theta) = R_0e^{b\theta}$" (Logarithmic spiral fits)
   - software: emcee
   - parameter: 40 walkers, 15,000 steps, 500 burn-in  
  > "The ensemble of 40 walkers is evolved for 15,000 steps. The first 500 steps are discarded as burn-in." (Logarithmic spiral fits)
   - fitting: Gaussian log-likelihood; flat priors on R0 (0 to R_dust) and b (-1 to 0 for Elias 27/IM Lup, 0 to 1 for WaOph 6); affine-invariant MCMC  
  > "Flat priors are adopted for $R_0$ and $b$." (Logarithmic spiral fits)
   - validation: Autocorrelation time generally <50 steps, much smaller than chain length  
  > "Convergence of the MCMC chains is evaluated by measuring the autocorrelation time (generally less than 50 steps)" (Logarithmic spiral fits)
5. **Measure spiral arm contrasts**: Ratio of arm peak intensity to 5th percentile 'background' in 1 au radial bins in deprojected image; errors propagated from image rms  
  > "The “background” intensity is estimated by taking the fifth percentile of the pixel intensity distribution in each bin." (3.4 Spiral arm contrasts)
   - parameter: Elias 27 contrasts from mid-res image (~80 mas beam)  
  > "For Elias 27 , the “mid-res” image ($\sim80$ mas beam) is used to estimate contrasts" (3.4 Spiral arm contrasts)
   - fitting: _not stated_
   - validation: Different percentile values give comparable contrasts; flux consistent with single-dish  
  > "Choosing slightly different percentile values to estimate the background leads to comparable contrast results." (3.4 Spiral arm contrasts)

## Software

- **CASA** : Calibration/imaging (multi-scale CLEAN)  
  > "`CASA` (cite: 2007ASPC..376..127M)" (Software)
- **emcee** : MCMC fitting of spiral models  
  > "The posterior probabilities are explored via the affine invariant MCMC sampler implemented in `emcee`" (Logarithmic spiral fits)
- **analysisUtils** : Listed in software  
  > "`analysisUtils` (<https://casaguides.nrao.edu/index.php/Analysis_Utilities>)" (Software)
- **AstroPy** : Listed in software  
  > "`AstroPy` (cite: 2013AA...558A..33A)" (Software)
- **scikit-image** : Listed in software  
  > "`scikit-image` (cite: scikit-image)" (Software)
- **SciPy** : Listed in software  
  > "`SciPy` (cite: scipy)" (Software)
- **matplotlib** : Plotting  
  > "`matplotlib` (cite: Hunter:2007)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Elias 27 S1 logarithmic pitch angle | 15.7 | ±0.2 | deg | 4 | / Elias 27 / S1 / $-131^\circ$ to $136^\circ$ / $110.9\pm0.6$ / $-0.282\pm0.004$ / $15.7\ensuremath{^\circ}\pm0.2\ensuremath{^\circ}$ / |
| Elias 27 S2 logarithmic pitch angle | 16.4 | ±0.2 | deg | 4 | $41.3\pm0.7$ / $-0.295\pm0.004$ / $16.4\ensuremath{^\circ}\pm0.2\ensuremath{^\circ}$ |
| IM Lup S1a pitch angle | 22 | ±2 | deg | 4 | / IM Lup / S1a / $55^\circ$ to $175^\circ$ / $94\pm7$ / $-0.40\pm0.04$ / $22^\circ\pm2^\circ$ / |
| IM Lup S1b pitch angle | 10 | ±1 | deg | 4 | / S1b / $-102^\circ$ to $0^\circ$ / $74.6\pm1.6$ / $-0.178\pm0.018$ / $10^\circ\pm1^\circ$ / |
| WaOph 6 S1 pitch angle | 13.4 | ±0.9 | deg | 4 | / WaOph 6 / S1 / $-112^\circ$ to $104^\circ$ / $45.9\pm0.9$ / $0.238\pm0.016$ / $13.4\ensuremath{^\circ}\pm0.9\ensuremath{^\circ}$ / |
| WaOph 6 S2 pitch angle | 13.7 | ±0.9 | deg | 4 | $0.244\pm0.016$ / $13.7\ensuremath{^\circ}\pm0.9\ensuremath{^\circ}$ |
| Spiral arm contrast range | generally 1.5 to 3 | not stated | dimensionless | 5 | All three disks exhibit moderate contrasts, generally between 1.5 and 3. |
| Spiral radial extent | Elias 27 R~50-230 au; IM Lup 25-110 au; WaOph 6 25-75 au | not stated | au | 1 | The spiral pattern in the Elias 27 disk extends from $R\sim50-230$ au |

## Qualitative findings

- All three disks have m=2 trailing spiral arms alongside annular substructures; IM Lup pitch angle decreases with radius.  
  > "All three disks feature $m=2$ spiral patterns in conjunction with annular substructures." (abstract)

## Claim tuples

- H: Are the continuum spiral arms trailing? | E: Use 12CO J=2-1 channel maps to find disk front side and rotation | R: Blue/red emission and tilt imply trailing arms in all three | F: Arms trail in all three disks | **supported**
- H: Do the arms have constant pitch angle? | E: Logarithmic and Archimedean spiral fits | R: Elias 27 and WaOph 6 approximated by logarithmic spirals; IM Lup S1a/S2a pitch twice S1b/S2b | F: IM Lup pitch angle decreases with radius | **supported**
- H: Are the spirals caused by companions or gravitational instability? | E: Compare pitch angles, contrasts, companion limits and disk properties to simulations | R: Pitch angles do not increase toward gaps; morphologies resemble GI simulations; no companions found | F: GI plausible; companions disfavoured but not excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Archimedean spirals preferred for simplicity since no feature spans more than a full winding  
  > "we prefer the simpler Archimedean parametrization because none of the spiral features are detected over more than a full winding" (3.3 Spiral arm pitch angles)
- Alternative: Shadowing from misaligned inner disk and stellar flybys disfavoured  
  > "the millimeter continuum observations of the disks in this work do not show evidence of misaligned inner disks." (Other hypotheses)
- How they decided it was enough: _not stated_
- Limitation (authors): Pitch angles uncertain because ring substructures or spurs complicate analysis  
  > "The pitch angles derived in this work need to be treated with caution" (Gravitational instability)
- Caveat (inferred, ours): Contrast as surface density proxy assumes optically thin emission and constant temperature/opacity
- Caveat (inferred, ours): Arm position uncertainty assumed equal to beam standard deviation
- Caveat (inferred, ours): Spiral positions depend on subtracted median profile and image taper
- Caveat (inferred, ours): Shortest-baseline filtering may affect Elias 27 contrasts

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Project codes and calibrated/self-calibrated data details
- Missing: Peak-finding code
- Missing: Spiral position tables
- Data volume (inferred): Hundreds of GB raw for several long-baseline execution blocks; DSHARP products much smaller
- Score (inferred): 3/5, Analysis on public DSHARP images with clear MCMC fits, but the pipeline for position extraction is not given and project codes are not printed.
- Rediscovery candidate: no, Project codes are not printed in the text and position-extraction details are missing.

## Links

- Method: (cite: 2018ApJ...869L..41A) (DSHARP overview: observations, calibration, imaging)
- Method: (cite: 2018ApJ...869L..42H) (Disk geometry and annular substructures)
- Companion: (cite: 2018ApJ...869L..44K) (Spirals in HT Lup A and AS 205 N)
- Companion: (cite: 2018ApJ...869L..47Z) (Planet-induced spiral and gap argument)
- Related: DSHARP

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00226.S",
  "2013.1.00498.S",
  "2013.1.00694.S",
  "2013.1.00798.S",
  "2016.1.00484.L"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 48,
  "rate": 0.571
 },
 "evidence_ok": true
}
```
