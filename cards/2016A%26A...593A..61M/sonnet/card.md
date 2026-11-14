# Dual differential polarimetry. A technique to recover polarimetric information from dual-polarization observations

`2016A&A...593A..61M` | Astronomy and Astrophysics 2016 | first author: Martí-Vidal, I. | arXiv: 1603.06072 | DOI: 10.1051/0004-6361/201628225

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type technical_calibration_or_instrument

## Science

- Fields: instrumentation, agn_and_quasars
- Question: Can polarimetric information of resolved sources be recovered from dual-polarization (XX, YY only) interferometric data using Earth-rotation synthesis of the parallactic angle?  
  > "it is still possible to obtain some polarimetry information from dual-polarization data." (Introduction)
- Target **3C 286 (ALMA SV, band 6)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **PKS 1830-211 (reanalysis)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00017.SV
- bands: Band 6 (225 GHz) for 3C 286  
  > "observations of source 3C 286 in band 6 (hereafter, we just refer to the central frequency in the observations, 225 GHz)" (4 Test with ALMA Science Verification data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- External data: CASA Guide 3C286 polarization results (p = 0.1645 ± 0.0002, angle 38.30 ± 0.02 deg) used as comparison  
  > "which is similar to the one reported in the CASA Guide ($p = 0.1645  \pm  0.0002$)" (4 Test with ALMA Science Verification data) [from CASA Guide; Nagai et al. 2016 (cite: Nagai)]
- External data: PKS 1830-211 ALMA data and RM results of earlier paper, reanalysed  
  > "In Fig. [7](#NEWSCI) we show the results of a reanalysis of the data reported in (cite: Science), but using the correct feed angles." (Reanalysis of Martí-Vidal et al. (2015)) [from (cite: Science)]
- External data: Beam squint estimates from ALMA Memo 362 Table VI  
  > "estimates of the beam squint (although in a circular polarization basis) are given in (cite: ALMA362) (Table VI)" (Effect of an off-axis receiver) [from (cite: ALMA362)]
- Simulation/model as data: Simulated ALMA observations (modified simobserve, alma.out04.cfg, 100 GHz, 10 GHz bandwidth) of M51 unpolarized plus compact polarized source, and extended Gaussian polarized source  
  > "Our simulation is based on the ALMA full array configuration “alma.out04.cfg”, given in the CASA database. The observing frequency was set to 100 GHz, with a bandwidth of 10 GHz." (3.1 Simulations)

## Processing

### Calibration

- pipeline or manual: Manual, following CASA Guide except gain type T and flux scaling with Ceres  
  > "We performed the bandpass and gain calibration as described in the CASA Guide of this SV dataset, with the exception that we applied the same amplitude solution to the two polarizations" (4 Test with ALMA Science Verification data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres  
  > "we used the absolute flux calibrator (Ceres)" (4 Test with ALMA Science Verification data)
- flux scale uncertainty: _not stated_
- self calibration: Two phase iterations and one amplitude iteration (T gain) on target  
  > "Two iterations of phase self-calibration and one iteration of amplitude self-calibration (in “T” gain type mode) were applied to the target" (4 Test with ALMA Science Verification data)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting (simulations)  
  > "The synthesized beam (using natural weighting) was 2.86$\times$2.50 arcsec" (3.1 Simulations)
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
- final beam: 2.86x2.50 arcsec, PA 89 deg (simulation)  
  > "The synthesized beam (using natural weighting) was 2.86$\times$2.50 arcsec, with a position angle, PA, of 89 degrees." (3.1 Simulations)
- final rms: _not stated_

### Inherited from earlier work

- SV 3C 286 calibration procedure  
  > "The full description of the data and the calibration procedure can be found in the CASA Guides database" (4 Test with ALMA Science Verification data) [from CASA Guide 3C286_Polarization; (cite: Nagai)]
- RM fitting approach for PKS 1830-211  
  > "This strategy was used by (cite: Science) to determine the $RM$ in the jet base of a distant active galactic nucleus" (Effects of Faraday rotation) [from (cite: Science)]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters (niter, threshold, masks) for simulations and 3C 286
- Scan/time binning used to define constant parallactic angle
- Noise levels in simulations
- In-house modified simobserve not available
- Details of the fit initial values and uncertainties for the PKS 1830-211 reanalysis
- Corrected feed angles and spectral windows/epochs used in reanalysis

## Analysis recipe

1. **Deconvolve Stokes I**: CLEAN deconvolution of full dataset without polarization calibration  
  > "we deconvolved the source structures (applying the CLEAN algorithm) using the complete set of observations" (Implementation of differential polarimetry in Fourier space)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit component fluxes per scan in XX and YY**: Visibility fitting of fixed-position CLEAN components, only flux densities free, per parallactic angle scan  
  > "The positions of all the components were fixed, and we only fit the flux densities." (Extended polarized emission)
   - software: uvmultifit
   - fitting: least squares, linear in visibility space  
  > "only the flux densities of the source components are fitted at each snapshot (so that the fitted source model is fully linear in visibility space)" (Implementation of differential polarimetry in Fourier space)
   - validation: _not stated_
3. **Compute Rpol and fit sinusoid vs parallactic angle**: Compute Rpol per pixel relative to fiducial source element and fit Rpol = pdif cos(2(phi-alpha-psi))  
  > "we computed $R^\psi_{pol}$ pixel by pixel for each parallactic angle and fit the results at each pixel to the model given in Eq." (Extended polarized emission)
   - assumption: Short baselines so parallactic angle is same for all antennas; for 3C 286, constant gain amplitude ratio and Ceres unpolarized  
  > "if we assume that the overall ratio of gain amplitudes in the array does not change significantly throughout the observations" (4 Test with ALMA Science Verification data)
   - fitting: least-squares minimization  
  > "we can recover the $p$ and $\phi$ distribution by means of a least-squares minimization" (Case 1. Perfect amplitude calibration)
   - validation: Compared with true model in simulations and CASA Guide for 3C 286  
  > "demonstrating the reliability of our differential polarization method" (Extended polarized emission)

## Software

- **CASA** : simulations, calibration, imaging  
  > "In all our simulations, we used the Common Astronomy Software Applications (CASA) package" (3.1 Simulations)
- **uvmultifit** : visibility fitting of component flux densities in XX and YY  
  > "we estimated the flux density of each source component, at each parallactic angle, using the visibility-fitting software `uvmultifit`" (Implementation of differential polarimetry in Fourier space)
- **simobserve** : in-house modified version for full-polarization synthetic data  
  > "The synthetic data were generated with an in-house modified version of the CASA task `simobserve`." (3.1 Simulations)
- **gaincal** : T-type gain solutions  
  > "(gain type “T” in the CASA task `gaincal`)" (4 Test with ALMA Science Verification data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 3C 286 fractional polarization | 0.189 | 0.001 | dimensionless | 3 | Our best-fit fractional polarization is $p = 0.189  \pm  0.001$ |
| 3C 286 polarization angle | 37.04 | 0.12 | deg | 3 | we obtain a source polarization angle of $\phi = 37.04 \pm 0.12$ deg. |
| PKS 1830-211 RM, 10 April 2012 (reanalysis) | 2.0e6 | 1.0e6 | rad/m^2 | 3 | $(2.0\pm1.0)\times10^6$ rad/m$^2$ and $(3.7\pm0.5)\times10^6$ rad/m$^2$ (observer’s frame) |
| PKS 1830-211 RM, 23 May 2012 (reanalysis) | 3.7e6 | 0.5e6 | rad/m^2 | 3 | $(2.0\pm1.0)\times10^6$ rad/m$^2$ and $(3.7\pm0.5)\times10^6$ rad/m$^2$ (observer’s frame) |

## Qualitative findings

- Rpol is insensitive to antenna polarization leakage (errors below 5e-4 for 1% leakage).  
  > "All errors are below 5$\times$10$^{-4}$." (Effects of polarization leakage)

## Claim tuples

- H: Dual differential polarimetry recovers polarization from XX/YY data | E: Simulations of extended unpolarized plus compact polarized source and extended polarized source | R: Rpol agrees with predictions; polarization angle swing reproduced | F: Technique reconstructs differential polarization distributions | **supported**
- H: Technique works on real ALMA data of a compact source | E: 3C 286 SV data using Ceres as reference | R: p=0.189 vs 0.1645 and angle 37.04 vs 38.30 deg from CASA Guide | F: Consistent absolute polarization recovered | **partially**
- H: Feed-angle error biased earlier PKS 1830-211 RMs | E: Reanalysis with correct feed angles | R: RMs 4.5 and 2.5 times lower for two epochs | F: Main conclusions of earlier paper unchanged | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Differential RM imaging with polarized fiducial element can be biased by up to ~30%.  
  > "the bias can be as large as $\sim30$%, even with wide fractional bandwidths" (Bias in the $RM$ differential imaging)
- Caveat (inferred, ours): The 3C 286 p differs from the CASA Guide by about 15%, larger than the quoted error
- Caveat (inferred, ours): Assumption of stable gain ratio is untested
- Caveat (inferred, ours): Simulation tests are idealized

## Reproducibility

- Data public (paper): ALMA SV data 2011.0.00017.SV; CASA Guide public  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00017.SV." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Modified simobserve
- Missing: CLEAN settings
- Missing: Scan definitions
- Data volume (inferred): ~10-50 GB for the 3C 286 SV dataset
- Score (inferred): 3/5, Public SV data and clear equations, but CLEAN and scan settings are missing and the simulation code is not released.
- Rediscovery candidate: yes, The SV data are public, the recipe is mostly clear, and the results are numeric (p and phi of 3C 286).

## Links

- Method: Martí-Vidal et al. 2014 (cite: UVM) (uvmultifit visibility fitting)
- Companion: Martí-Vidal et al. 2015 (cite: Science) (First application to PKS 1830-211, reanalysed here)
- Related: ALMA Science Verification 3C 286 polarization

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
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
  "facts": 68,
  "stated": 27,
  "rate": 0.397
 },
 "evidence_ok": true
}
```
