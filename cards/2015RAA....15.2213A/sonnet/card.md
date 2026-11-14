# <SUP>12</SUP>CO emission from the Red Rectangle

`2015RAA....15.2213A` | Research in Astronomy and Astrophysics 2015 | first author: Anh, Pham Tuan | arXiv: 1503.00858 | DOI: 10.1088/1674-4527/15/12/009

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: evolved_stars
- Question: What are the morphology, temperature, density and kinematics of the CO gas envelope of the Red Rectangle, from archival ALMA CO(3-2) and CO(6-5) data?  
  > "ALMA observations of the CO emission of the Red Rectangle, of an unprecedented quality, have been analysed with the aim to reveal the main features of the morphology and kinematics of the gas envelope." (SUMMARY AND CONCLUSIONS)
- Target **Red Rectangle (HD 44179)**: coordinates _not stated_; z/distance 710 pc  
  > "the star is usually considered as being 710 pc away from Earth, see Men’shchikov et al. 2002" (MAIN FEATURES); distance from Men'shchikov et al. 2002  
  > "the star is usually considered as being 710 pc away from Earth, see Men’shchikov et al. 2002" (MAIN FEATURES)

## Data provenance

- ALMA projects: 2011.0.00223.S
- bands: CO(3-2) (345 GHz) and CO(6-5) (690 GHz)  
  > "at 345 GHz, $\sigma_y$=0.26$''$ and $\sigma_z$=0.23$''$ and at 690 GHz" (CONTINUUM AND DUST)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: configuration extending up to 380 m, 21 to 24 active antennas  
  > "with only 21 to 24 active antennas in a configuration that extended up to only 380 m" (SUMMARY AND CONCLUSIONS)
- angular resolution: 0.50''x0.49'' (CO 3-2); 0.27''x0.24'' (CO 6-5)  
  > "The synthetic beam sizes are 0.50$''$$\times$0.49$''$ and 0.27$''$$\times$0.24$''$ for CO(3-2) and CO(6-5) respectively." (DATA)
- max recoverable scale: _not stated_
- sensitivity: rms 20 mJy/beam (CO 3-2), 72 mJy/beam (CO 6-5)  
  > "Gaussian fits give rms values of 20 mJy/beam for CO(3-2) and 72 mJy/beam for CO(6-5)" (DATA)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Public archival data  
  > "have been recently released for public access" (DATA)
- Line: CO J=3-2 (not stated)
- Line: CO J=6-5 (not stated)
- External data: Dust temperature and CO density model for comparison  
  > "the dust temperature quoted by Men’shchikov et al. (2002) decreases from $\sim$80 K at $r$=1$''$ to $\sim$60 K at $r$=2.5$''$" (TEMPERATURE AND DENSITY DISTRIBUTIONS) [from Men’shchikov et al. 2002]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Data used in the form provided by ALMA staff  
  > "we use the data in the form provided by the ALMA staff, which are of a quality sufficient for the purpose of the present study" (DATA)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
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
- final beam: _not stated_
- final rms: 20 mJy/beam (3-2), 72 mJy/beam (6-5)  
  > "Gaussian fits give rms values of 20 mJy/beam for CO(3-2) and 72 mJy/beam for CO(6-5)" (DATA)

### Inherited from earlier work

- Details of data collection and calibration  
  > "Details of data collection are given in Appendix A of Bujarrabal et al. (2013b) and do not need to be repeated here" (DATA) [from Bujarrabal et al. (2013b)]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging software/CASA version and parameters of the archive-delivered cubes
- Exact regridding/rotation interpolation method
- Initial guesses and optimizer for chi2 minimization
- Rest frequencies used
- Observing dates and times on source

## Analysis recipe

1. **Regrid and select data**: Rearrange cubes to 50x50 pixels, 5''x5'', 36 velocity bins of 0.40 km/s, rotated 13 deg, centred on continuum; keep pixels above flux thresholds (1526 pixels)  
  > "we have rearranged both CO(3-2) and CO(6-5) data in a common array of 50$\times$50 pixels centred on the continuum emission of the star" (DATA)
   - parameter: thresholds 0.75 and 3.0 Jy km/s arcsec^-2  
  > "more than 0.75 Jy$\times$kms$^{-1}$$\times$arcsec$^{-2}$ in the CO(3-2) data sample and more than 3.0" (DATA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Reconstruct effective density**: Iteratively solve F(y,z)=∫ρ(ξ,z)dx assuming rotational symmetry, 35 ξ bins x 50 z bins of 0.1''  
  > "The integral equation is solved by iteration, using as input the fluxes, integrated over Doppler velocities, measured in each of the 1526 pixels that have been retained." (GAS EFFECTIVE DENSITY)
   - parameter: uncertainties: absolute 0.16 (3-2) and 2.2 (6-5) Jy arcsec^-2 plus 20% relative; ten iterations  
  > "Ten iterations are amply sufficient to achieve convergence." (GAS EFFECTIVE DENSITY)
   - assumption: Rotational symmetry, negligible absorption, LTE  
  > "The assumption of rotational invariance about the star axis implies in addition that absorption is negligible." (MAIN FEATURES)
   - fitting: chi2 minimization  
  > "The iterative process is stopped when the value of $\chi^2$ used to measure the quality of the agreement" (GAS EFFECTIVE DENSITY)
   - validation: Compared observed and reintegrated flux densities in 8 R and 8 angle bins  
  > "we compare in Figure 5 the observed flux densities with those obtained by integration of the effective densities along the line of sight" (GAS EFFECTIVE DENSITY)
3. **Derive temperature from CO ratio**: k_BT=(E6-E3)/ln(C/R_T) with (E6-E3)/kB=82.5 K, C=15.6  
  > "In the present case, $(E_6-E_3)/k_B$=82.5 K and $C$=15.6." (TEMPERATURE AND DENSITY DISTRIBUTIONS)
   - assumption: LTE, optically thin  
  > "In a regime of thermal equilibrium, and in the absence of significant absorption" (TEMPERATURE AND DENSITY DISTRIBUTIONS)
   - fitting: _not stated_
   - validation: Compared with Men'shchikov et al. 2002 dust temperature and CO density  
  > "It is in good agreement with a model (Men’shchikov et al. 2002)" (TEMPERATURE AND DENSITY DISTRIBUTIONS)
4. **Fit kinematic model**: Joint chi2 fit of equatorial rotation+expansion and parabolic polar outflow model to velocity spectra of both lines  
  > "we fit both sets of data jointly, each set being given the effective densities obtained in the preceding section." (GAS VELOCITY)
   - parameter: R in [0.2'',2.5''], r in [0.2'',3.5'']  
  > "We require $R$ to be in the interval \[0.2$''$, 2.5$''$\] and $r$ in the interval \[0.2$''$, 3.5$''$\]." (GAS VELOCITY)
   - fitting: chi2 minimization; parameter ranges where chi2 rises <5%  
  > "$\chi^2$ does not exceed its minimal value by more than 5%" (GAS VELOCITY)
   - validation: Grouped spectra comparison in Figure 11  
  > "The quality of the fit is surprisingly good in view of the crudeness of the model." (GAS VELOCITY)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Average temperature | 63 | not stated | K | 3 | their ratio, 4.3, corresponds to an average temperature of 63 K |
| Rotation velocity V_rot | 0.99 | +0.15/-0.14 | km/s | 4 | / P / 0.81 / 0.99 / 1.03 / 6.3 / 1.56 / 8 / 1.4 / 1.0 / |
| Polar outflow velocity V_out | 6.3 | +0.8/-0.7 | km/s | 4 | / P / 0.81 / 0.99 / 1.03 / 6.3 / 1.56 / 8 / 1.4 / 1.0 / |
| Star-axis inclination | 8 | not stated | deg | 4 | the star axis is inclined by $\sim$8$^\circ$ from the North away the Earth |
| Continuum flux 345 GHz | 0.66 | 0.10 | Jy | 0 | The integrated fluxes are 0.66$\pm$0.10 Jy at 345 GHz and 4.0$\pm$0.6 Jy at 690 GHz |
| Continuum flux 690 GHz | 4.0 | 0.6 | Jy | 0 | The integrated fluxes are 0.66$\pm$0.10 Jy at 345 GHz and 4.0$\pm$0.6 Jy at 690 GHz |

## Qualitative findings

- South-east excess of effective density up to ~70% in the bicone region  
  > "The main feature is an important south-east excess, particularly enhanced in the region of the bicone where it reaches $\sim$70%." (ASYMMETRIES)

## Claim tuples

- H: Does the gas have distinct equatorial and polar kinematics? | E: Joint kinematic model fit to CO(3-2) and CO(6-5) cubes | R: Rotation ~1 km/s at 1'' with expansion ~1.6 km/s; polar outflow ~6-7 km/s | F: Equatorial rotating, expanding torus and parabolic polar outflow are separated by z^2/ξ=0.81'' | **supported**
- H: Does the CO temperature differ between outflow and equator? | E: CO(6-5)/CO(3-2) effective density ratio | R: Equator ~60 to 50 K; outflow ~200 K at 0.3'' falling to ~80 K at 1.5'' | F: Outflow hotter near star | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Simplicity with limited ambitions, using ALMA-processed images  
  > "The analysis was performed in a spirit of simplicity, with limited ambitions in terms of precision and sensitivity" (SUMMARY AND CONCLUSIONS)
- Alternative: Radial outflow gave worse results than parabolic flow  
  > "it gives significantly better results than a radial outflow" (GAS VELOCITY)
- How they decided it was enough: _not stated_
- Limitation (authors): Imperfect deconvolution/calibration and crude symmetry and optically thin assumptions  
  > "most of the flux fluctuations observed here arise from imperfect deconvolution and/or calibration" (DATA)
- Caveat (inferred, ours): Uses non-reprocessed archive images with higher noise
- Caveat (inferred, ours): LTE and optically thin assumptions untested; 13CO not used
- Caveat (inferred, ours): No formal uncertainties on fit parameters
- Caveat (inferred, ours): Rotational symmetry broken by large asymmetry

## Reproducibility

- Data public (paper): Released for public access  
  > "have been recently released for public access" (DATA)
- Products in archive: _not stated_
- Missing: Code for integral-equation solution and fits
- Missing: Exact pixel selection/regridding procedure
- Data volume (inferred): ~1-5 GB
- Score (inferred): 3/5, Public data and clear equations, but no code, software or optimizer details.
- Rediscovery candidate: yes, Public data, numeric results, and well-specified model equations.

## Links

- Method: Bujarrabal et al. (2013b) (Data collection details and reprocessed images)
- Companion: Bujarrabal et al. (2013b) (Preliminary ALMA analysis of same data)

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 31,
  "rate": 0.477
 },
 "evidence_ok": true
}
```
