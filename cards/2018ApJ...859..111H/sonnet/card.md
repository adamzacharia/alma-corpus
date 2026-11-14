# The Circumstellar Disk and Asymmetric Outflow of the EX Lup Outburst System

`2018ApJ...859..111H` | The Astrophysical Journal 2018 | first author: Hales, A. S. | arXiv: 1804.10340 | DOI: 10.3847/1538-4357/aac018

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What are the dust and gas disk properties of EX Lup, and does it show outflow or non-Keplerian structure, in the context of FUor/EXor outbursts?  
  > "The circumstellar disk of EX Lup is resolved for the first time in 1.3 mm continuum emission and in the $J$=2–1 spectral line of three isotopologues of CO." (abstract)
- Target **EX Lup**: coordinates RA 16:03:05.479, Dec -40:18:25.789  
  > "Ra$^{a}$ | 16:03:05.479" (Table 1); "Distance: $d$ (pc) | 155 | (cite: lombardi2008)" (Table 3); z/distance 155 pc  
  > "Ra$^{a}$ | 16:03:05.479" (Table 1); "Distance: $d$ (pc) | 155 | (cite: lombardi2008)" (Table 3); distance from Lombardi et al. 2008 (cite: lombardi2008)  
  > "Ra$^{a}$ | 16:03:05.479" (Table 1); "Distance: $d$ (pc) | 155 | (cite: lombardi2008)" (Table 3)

## Data provenance

- ALMA projects: 2015.1.00200.S
- bands: Band 6 (~230 GHz)  
  > "ALMA observations of EX Lup using the facility Band 6 ($\sim$ 230 GHz) receivers were acquired on 25 July 2016" (Observations)
- frequencies and spectral setup: Four FDM line windows (12CO, 13CO, C18O 2-1, 13CO v=1) plus one TDM continuum window at 232.477 GHz  
  > "A fifth spectral window configured in Time Division Mode (TDM) was positioned in a region devoid of line emission for detecting the continuum dust emission (centered at 232.477 GHz/1.29 mm)." (Observations)
- continuum bandwidth: 1.875 GHz  
  > "and 1.875 GHz for the continuum." (Observations)
- arrays: 12-m array, 40 antennas  
  > "utilizing interferometric observations on 40 antennas in the main 12-meter antenna array" (Observations)
- configurations: _not stated_
- baselines: 15.1 m to 1.12 km  
  > "providing baselines ranging from 15.1 m to 1.12 km" (Observations)
- angular resolution: ~0.3" (~45 au)  
  > "yields an angular resolution of $\sim$ 0.3$\ensuremath{''}$ ($\sim$ 45 au)" (Observations)
- max recoverable scale: ~3.2" (~500 au)  
  > "Maximum Recoverable Scale (MRS; see (cite: schieven2017)) of $\sim$ 3.2$\ensuremath{''}$ ($\sim$ 500 au)" (Observations)
- sensitivity: Continuum RMS 0.038 mJy/beam; 12CO 4.5 mJy/beam per 0.2 km/s channel  
  > "RMS (mJy beam$^{-1}$) | 0.038 | 0.1 | 4.5 | 3.6 | 2.2" (Table 1)
- time on source: 28.3 minutes  
  > "The total time spent on-source was 28.3 minutes." (Observations)
- observing dates: 25 July 2016 (Cycle 3)  
  > "were acquired on 25 July 2016 (during ALMA Cycle 3)" (Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Line: 13CO J=2-1 (220.399 GHz)
- Line: C18O J=2-1 (219.560 GHz)
- Line: 13CO J=2-1, v=1 (218.437 GHz)
- External data: Stellar parameters: M=0.5 Msun, Teff=3859 K, R=0.8 Rsun  
  > "Primary Star Mass: $M_\star$ (M$_{\odot}$) | 0.5 | (cite: frasca2017)" (Table 3) [from (cite: frasca2017)]
- External data: Disk flaring index psi=1.09  
  > "with a flaring index $\psi$ = 1.09 as determined by (cite: sipos2009)" (4.1 Radiative Transfer Modelling of Dust Continuum) [from (cite: sipos2009)]
- External data: Distance 155 pc  
  > "Distance: $d$ (pc) | 155 | (cite: lombardi2008)" (Table 3) [from (cite: lombardi2008)]
- External data: Grid of disk models for 13CO/C18O mass estimate  
  > "(cite: williams2014) developed a grid of protoplanetary disk models that can be used to derive disk masses based on the $^{13}$CO(2–1) to C$^{18}$O(2–1) integrated line ratios" (5.2 CO Gas Disk) [from (cite: williams2014)]

## Processing

### Calibration

- pipeline or manual: ALMA Science Pipeline, run by East Asia ARC staff  
  > "All data were calibrated using the ALMA Science Pipeline (version r36660 of Pipeline-Cycle3-R4-B release)" (Observations)
- casa version: _not stated_
- pipeline version: r36660 of Pipeline-Cycle3-R4-B  
  > "version r36660 of Pipeline-Cycle3-R4-B release" (Observations)
- archive products used as is: _not stated_
- flux calibrator: J1427-4206, flux interpolated between Band 3 and Band 7 monitoring (spectral index -0.54±0.05)  
  > "The Band 3 to Band 7 spectral index used for the interpolation was -0.54 (uncertainty $\pm~$0.05)." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: Single iteration of phase-only self-calibration on continuum; SNR improved by 1.8; tables applied to line windows  
  > "A single iteration of phase-only self-calibration was performed to improve the coherence in the final image." (Observations)

### Imaging

- task: CASA clean  
  > "Imaging of the continuum and molecular emission lines was performed using the clean task in CASA." (Observations)
- deconvolver: _not stated_
- weighting robust: Continuum: Briggs robust 0.5; CO cubes natural weighting (extra 12CO cube robust 0.5)  
  > "clean was run with natural weighting to maximize sensitivity." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: In visibility domain before line imaging  
  > "Continuum subtraction in the visibility domain was performed prior to imaging of each molecular line." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Spectral binning to 0.2 (12CO), 0.3 (13CO), 0.8 km/s (C18O, 13CO v=1)  
  > "to 0.3 km s$^{-1}$ for $^{13}$CO(2–1), and to 0.8 km s$^{-1}$ for C$^{18}$O(2–1)" (Observations)
- final beam: Continuum 0.32"x0.26" PA 61.8°; 12CO natural 0.39"x0.29" PA 62.7°  
  > "resulting in a synthesized beam size of 0.32$\ensuremath{''}\times$0.26$\ensuremath{''}$ at position angle PA = 61.8$^{\circ}$ in the final continuum image." (Observations)
- final rms: Continuum 0.038 mJy/beam; 12CO 4.5; 13CO 3.6; C18O 2.2 mJy/beam per channel  
  > "RMS (mJy beam$^{-1}$) | 0.038 | 0.1 | 4.5 | 3.6 | 2.2" (Table 1)

### Inherited from earlier work

- Dust modeling procedure similar to that used for other FUor/EXor sources  
  > "The modeling procedure applied to EX Lup is similar to the one we performed for other FUor/EXor sources (cite: cieza2017), allowing direct comparison." (5.1 Dust Disk) [from (cite: cieza2017)]
- Tapered-edge surface density model  
  > "We adopt the standard tapered-edge model to describe the surface density profile (cite: andrews2009; williams11)" (4.1 Radiative Transfer Modelling of Dust Continuum) [from (cite: andrews2009; williams11)]
- Model visibilities computed via FFT and interpolation to uv points  
  > "The model visibilities were obtained by taking the Fast Fourier Transform of model images and interpolating to the same $uv$ points as the observations (cite: marino)." (4.1.1 Fitting Procedure) [from (cite: marino)]
- Genetic algorithm for CO model fitting  
  > "We used a genetic algorithm (cite: mathews2013; pinte2018) to fit the $^{13}$CO and C$^{18}$O moment 0 maps simultaneously." (4.2 Comparison with Axisymmetric CO Gas Disk Model) [from (cite: mathews2013; pinte2018)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum subtraction in the CO windows
- Self-calibration solution interval and reference antenna
- Clean masks, thresholds, cell and image sizes
- Rest-frame/velocity reference and range used for moment maps
- Apertures/thresholds for moment maps (clip level)
- Gas model fixed parameters beyond those listed (e.g., grid, photon packets)
- Dust model vertical structure H100 treatment and fit visibility weighting

## Analysis recipe

1. **Calibrate and image continuum and CO lines**: ALMA pipeline calibration, phase-only self-cal, CASA clean for continuum and cubes  
  > "Self-calibration tables derived from the continuum were applied to the FDM spectral windows before imaging the CO lines." (Observations)
   - software: CASA
   - parameter: Continuum Briggs robust 0.5; lines natural weighting  
  > "imaged using Briggs weighting with a robust parameter of 0.5" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum size, flux, inclination, spectral index**: Elliptical Gaussian fit in image plane; inclination from axis ratio assuming circular disk  
  > "The parameters of the compact continuum emission can be determined from elliptical Gaussian fitting in the image domain using the CASA task imfit." (3.1 Dust Continuum Emission)
   - software: CASA imfit
   - assumption: Deprojected disk is circular  
  > "Assuming that the deprojected EX Lup disk is circular, the major/minor axis ratio implies a disk inclination angle of 32.4$^{\circ}~\pm~$0.9$^{\circ}$." (3.1 Dust Continuum Emission)
   - fitting: _not stated_
   - validation: Residual after Gaussian subtraction shows no emission above 5-sigma  
  > "There is no evidence of residual emission above 5-$\sigma$ after subtracting the best-fit elliptical Gaussian from the continuum image." (3.1 Dust Continuum Emission)
3. **Kinematic analysis of CO: PA, centroids, PV diagrams, inclination**: Channel-map astrometry with chi2 fit for PA; PV diagrams along PA 78°; Keplerian fit to red-side centroid velocities for inclination  
  > "In Figure [8](#fig-angle) we use the red-shifted data points from the inner $r~<~$100 au from Figure [7](#fig-pv-co) to fit the inclination angle, assuming Keplerian rotation around a star of mass 0.5 M$_{\odot}$." (3.2 Spectral Line Emission)
   - parameter: Channels with SNR>5 used for astrometry  
  > "Only channels where the emission has an SNR $>$ 5 were included in the fit." (3.2 Spectral Line Emission)
   - assumption: Stellar mass 0.5 Msun  
  > "assuming Keplerian rotation around a star of mass 0.5 M$_{\odot}$" (3.2 Spectral Line Emission)
   - fitting: chi2 fitting  
  > "The inclination angle derived from ${\chi}^2$ fitting is 38$^{\circ}~\pm~$4" (3.2 Spectral Line Emission)
   - validation: Compared with Kospal et al. 2016b inclination  
  > "thus consistent with the value derived by (cite: kospal2016b)." (3.2 Spectral Line Emission)
4. **Radiative transfer fit of dust continuum for dust mass and structure**: RADMC-3D tapered-edge disk model fit to visibilities with emcee  
  > "The model and the data (the self-calibrated Measurement Set including only the continuum) were compared in the $uv$ plane." (4.1.1 Fitting Procedure)
   - software: RADMC-3D, emcee
   - parameter: 500 walkers, 1000 iterations; uniform priors on Md, gamma, Rc, H100  
  > "after running 1000 iterations ($\sim$ 10 times the autocorrelation time) with 500 walkers." (4.1.1 Fitting Procedure)
   - assumption: Grain sizes 0.1 um to 3 mm, n(a)∝a^-3.5; 30% amorphous carbon/70% astrosilicate; kappa_1.3mm=2.2 cm2/g; Tstar=3859 K, R=0.8 Rsun; Rin 0.05 au; gas-to-dust 100  
  > "We used a standard mix of 30$\%$ amorphous carbons and 70$\%$ astro-silicates." (4.1 Radiative Transfer Modelling of Dust Continuum)
   - fitting: Affine-invariant MCMC, likelihood ∝ exp(-chi2/2), uniform priors  
  > "The likelihood function is proportional to $\exp(-\chi^2/2)$" (4.1.1 Fitting Procedure)
   - validation: Model compared to resolved 1.3 mm image  
  > "Figure [1](#fig-0) shows that our model fits the resolved image of the disk at 1.3 mm" (4.1 Radiative Transfer Modelling of Dust Continuum)
5. **Fit CO gas disk model to 13CO and C18O moment 0**: MCFOST models in LTE, genetic algorithm fit to moment 0 maps; synthetic visibilities via simobserve and clean  
  > "The model images were used to create synthetic visibilities using CASA task simobserve" (4.2 Comparison with Axisymmetric CO Gas Disk Model)
   - software: MCFOST, CASA simobserve
   - parameter: 100 models per generation, 50 generations; Rc fixed 75 au, Rout 150 au  
  > "Each generation was composed of 100 models and the genetic algorithm was run for 50 generations." (4.2 Comparison with Axisymmetric CO Gas Disk Model)
   - assumption: LTE with Tgas=Tdust; CO/H2 = 1e-4; freeze-out below 20 K with depletion factor 1000  
  > "Freeze-out of CO molecules onto dust grains was assumed to occur at temperatures below 20 K with a depletion factor of 1000." (4.2 Comparison with Axisymmetric CO Gas Disk Model)
   - fitting: Genetic algorithm over Mgas, gamma, Rin, H100, flaring  
  > "The following parameters were allowed to vary during the fitting process: $M_{\rm gas}$, $\gamma$, $R_{\rm in}$, H$_{100}$ as well as the disk’s flaring exponent." (4.2 Comparison with Axisymmetric CO Gas Disk Model)
   - validation: Residual moment 0 images; cross-check of mass with Williams & Best 2014 line-ratio grid  
  > "we obtain a total disk mass of 5.4$\times10^{-4}$ M$_\odot$." (5.2 CO Gas Disk)

## Software

- **CASA** : Calibration, clean imaging, imfit, simobserve  
  > "Imaging of the continuum and molecular emission lines was performed using the clean task in CASA." (Observations)
- **RADMC-3D** : Dust continuum radiative transfer  
  > "the continuum was modeled using the radiative transfer code radmc-3d (cite: Dullemond2012)" (4.1 Radiative Transfer Modelling of Dust Continuum)
- **emcee** : MCMC sampling of dust model posterior  
  > "We used the latter’s publicly available python module emcee to sample the parameter space" (4.1.1 Fitting Procedure)
- **MCFOST** : CO line radiative transfer models  
  > "we use the three-dimensional Monte Carlo radiative transfer code mcfost (cite: pinte2006; pinte2009)" (4.2 Comparison with Axisymmetric CO Gas Disk Model)
- **Astropy** : General analysis  
  > "This research made use of astropy, a community-developed core python package for astronomy" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.29 mm total flux | 17.37 | 0.15 | mJy | 2 | with a total 1.29 mm flux of 17.37$~\pm~$0.15 mJy |
| Continuum inclination | 32.4 | 0.9 | deg | 2 | implies a disk inclination angle of 32.4$^{\circ}~\pm~$0.9$^{\circ}$ |
| Spectral index 1.30-1.37 mm | 2.19 | 0.47 | dimensionless | 2 | This results in a spectral index (F$_\nu\propto\nu^\alpha$) between 1.30 and 1.37 mm of 2.19$~\pm~$0.47. |
| 12CO integrated flux | 5011 | 510 | mJy km/s | 3 | The $^{12}$CO integrated line emission is 5011 $\pm$ 510 mJy km s$^{-1}$ |
| CO-kinematics inclination (Keplerian, M=0.5 Msun) | 38 | 4 | deg | 3 | The inclination angle derived from ${\chi}^2$ fitting is 38$^{\circ}~\pm~$4 |
| Dust disk characteristic radius | 22.9 | +1.2/-0.9 | au | 4 | Characteristic Radius: $R_{\rm {c}}$ (au) / 75 / $22.9^{+1.2}_{-0.9}$ |
| Dust mass | 1.1e-4 | ±0.3e-4 | Msun | 4 | Disk Dust Mass: $M_{\rm d}$ (M$_{\odot}$) / $1.1\times 10^{-4}$ / $1.1^{+0.3}_{-0.3}\times 10^{-4}$ |
| Gas disk mass | 5.1e-4 | not stated | Msun | 5 | Disk Total Mass: $M_{\rm D}$ (M$_{\odot}$) / $5.1\times10^{-4}$ / 100 $\times$ $M_{\rm d}$ |
| Gas-to-dust ratio | 4.5 | not stated | dimensionless | 5 | our gas mass estimates imply a gas-to-dust ratio of 4.5 |

## Qualitative findings

- 12CO disk is asymmetric with the blue side deviating from Keplerian rotation; a blue-shifted arc 0.8" NW is interpreted as an outflow cavity wall  
  > "We interpret this extended structure as the brightened walls of a cavity excavated by an outflow, which are more commonly seen in FUor sources." (abstract)

## Claim tuples

- H: Does the EX Lup dust disk show substructure or asymmetries? | E: Gaussian fit and RT modeling of 1.3 mm continuum | R: Compact disk, Rc~23 au, no residuals above 5 sigma | F: Compact smooth dust disk with Md ~1e-4 Msun | **supported**
- H: Is there an outflow in the EXor EX Lup? | E: 12CO channel maps and PV diagrams | R: Blue-shifted arc-like emission 0.8" NW | F: Outflow phenomenon persists into the EXor phase | **supported**
- H: What is the gas disk mass? | E: MCFOST fit to 13CO and C18O moment 0 maps | R: Mgas 5.1e-4 Msun, gas-to-dust ratio 4.5 | F: Low gas-to-dust ratio, possibly CO depletion; mass may be a lower limit | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Asymmetry origin alternatives (companion, planet circumplanetary disk, instability) not ruled out  
  > "However ruling out other possible explanations such disk instabilities, disk-companion interactions, or optical depth effects requires further modeling." (6 Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Possible resolved-out large-scale 12CO emission; no single-dish data  
  > "Unfortunately, there are no $^{12}$CO(2–1) single-dish observations available which could have been used to estimate the amount of resolved-out emission." (5.3 Widespread 12CO(2–1) Gas Emission)
- Limitation (authors): Genetic algorithm solution may not be unique  
  > "the solution found by the genetic algorithm may not be unique" (4.2 Comparison with Axisymmetric CO Gas Disk Model)
- Caveat (inferred, ours): Dust mass depends on assumed opacity and optically thick inner disk (factor 2-5)
- Caveat (inferred, ours): Rc and Rout of gas model fixed by eye
- Caveat (inferred, ours): Single short observation; systemic velocity ambiguous
- Caveat (inferred, ours): No error bars on gas model parameters

## Reproducibility

- Data public (paper): Project code cited; archival ALMA data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA.2015.1.00200.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean masks, thresholds, image sizes
- Missing: Line-free channels
- Missing: Self-cal details
- Missing: Marino visibility-modeling code (in preparation)
- Data volume (inferred): ~50-100 GB raw for one Band 6 execution
- Score (inferred): 3/5, Data public and standard tools, but several imaging and modeling settings unstated and one code unpublished.
- Rediscovery candidate: no, Key results rely on custom RT modeling with an unpublished visibility code and unstated imaging details.

## Links

- Method: (cite: pinte2018) (Genetic algorithm fitting)
- Method: (cite: williams2014) (CO line-ratio disk mass grids)
- Companion: (cite: cieza2017) (Same dust modeling approach for other FUor/EXor sources)
- Companion: (cite: kospal2016b) (Single-dish CO detection of EX Lup)
- Related: SOLA (Soul of Lupus with ALMA)

## Checks

```json
{
 "quotes": 83,
 "quotes_ok": 83,
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
  "facts": 83,
  "stated": 62,
  "rate": 0.747
 },
 "evidence_ok": true
}
```
