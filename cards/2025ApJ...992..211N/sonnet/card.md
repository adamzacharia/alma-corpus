# Revisiting the Supermassive Black Hole Mass of NGC 7052 Using High Spatial Resolution Molecular Gas Observed with ALMA

`2025ApJ...992..211N` | The Astrophysical Journal 2025 | first author: Ngo, Hai N. | arXiv: 2509.02956 | DOI: 10.3847/1538-4357/ae0455

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What is the SMBH mass and stellar I-band M/L of NGC 7052 from 12CO(2-1) kinematics at 0.3 arcsec resolution, with an improved stellar plus molecular gas mass model?  
  > "We employ this technique in this work to revisit the dynamical-$M_{\rm BH}$ estimate in NGC 7052 based on our own 0.29$''$ $\times$ 0.22$''$ synthesis beamsize ALMA observation" (Introduction)
- Target **NGC 7052**: coordinates RA 21h18m33.0380s, Dec +26d26m49.030s  
  > "Given a distance of $D=69.3$ Mpc to NGC 7052 (cite: Ma14), the physical scale for converting between arcseconds ($''$) and parsecs (pc) is 336 pc/$''$." (Introduction); "NGC 7052 (R.A., Decl. = $21^{\rm h}18^{\rm m}33.0380s$, ${+}26\ensuremath{^\circ}26\ensuremath{'}49.030\ensuremath{''}$)" (1.1 The galaxy NGC 7052); z/distance D = 69.3 Mpc; z ≈ 0.015584  
  > "Given a distance of $D=69.3$ Mpc to NGC 7052 (cite: Ma14), the physical scale for converting between arcseconds ($''$) and parsecs (pc) is 336 pc/$''$." (Introduction); "NGC 7052 (R.A., Decl. = $21^{\rm h}18^{\rm m}33.0380s$, ${+}26\ensuremath{^\circ}26\ensuremath{'}49.030\ensuremath{''}$)" (1.1 The galaxy NGC 7052); distance from Ma14 (MASSIVE survey, redshift-based)  
  > "Given a distance of $D=69.3$ Mpc to NGC 7052 (cite: Ma14), the physical scale for converting between arcseconds ($''$) and parsecs (pc) is 336 pc/$''$." (Introduction); "NGC 7052 (R.A., Decl. = $21^{\rm h}18^{\rm m}33.0380s$, ${+}26\ensuremath{^\circ}26\ensuremath{'}49.030\ensuremath{''}$)" (1.1 The galaxy NGC 7052)

## Data provenance

- ALMA projects: 2019.1.00036.S
- bands: Band 6  
  > "The observations were conducted in Band 6 using four frequency division mode (FDM) spectral windows (SPWs), each spanning 2 GHz in width." (2 ALMA observation and reduction)
- frequencies and spectral setup: 4 FDM SPWs of 2 GHz, 1920 channels, 976.562 kHz (~1.3 km/s) channels; one SPW on CO(2-1) (230.538 GHz), three for continuum  
  > "Each SPW is divided into 1920 channels along the frequency dimension with a channel width of 976.562 kHz ($\approx$1.3 km s$^{-1}$)." (2 ALMA observation and reduction)
- continuum bandwidth: _not stated_
- arrays: 39 12-m antennas  
  > "using 39 12-m antennas in the C-6 configuration" (2 ALMA observation and reduction)
- configurations: C-6  
  > "using 39 12-m antennas in the C-6 configuration" (2 ALMA observation and reduction)
- baselines: 15 m to 2.5 km  
  > "The baselines ranged from 15 m to 2.5 km" (2 ALMA observation and reduction)
- angular resolution: 0.29" x 0.22" (continuum); 0.31" x 0.23" (CO cube)  
  > "which has a synthesized beamsize of $\theta_{\rm FWHM} = 0.31\ensuremath{''} \times 0.23\ensuremath{''}$" (2.2 CO emission imaging)
- max recoverable scale: ≈4.7"  
  > "a maximum recoverable scale of MRS $\approx4.7\ensuremath{''}$" (2 ALMA observation and reduction)
- sensitivity: 79 uJy/beam continuum; 0.5 mJy/beam per 10 km/s CO  
  > "Sensitivity (mJy beam$^{-1}$ per 10 km s$^{-1}$) |                0.5" (Table 2)
- time on source: 2509 s  
  > "The total on-source integration time was 2509 seconds on June 27, 2021." (2 ALMA observation and reduction)
- observing dates: June 27, 2021  
  > "The total on-source integration time was 2509 seconds on June 27, 2021." (2 ALMA observation and reduction)
- pi or archival as stated: PI Dieu Nguyen (author's own program)  
  > "as part of project 2019.1.00036.S (PI: Dieu Nguyen)" (2 ALMA observation and reduction)
- Line: 12CO J=2-1 (230.538 GHz)
- Other facility **HST/WFPC2 WFC F814W**: Image used to derive improved stellar MGE mass model  
  > "we utilized the Wide Field Camera (WFC) instead of the PC, providing a larger FoV of $80\ensuremath{''} \times 80\ensuremath{''}$" (3.2 Our improved stellar-mass model)
- External data: Distance 69.3 Mpc  
  > "Given a distance of $D=69.3$ Mpc to NGC 7052 (cite: Ma14)" (Introduction) [from (cite: Ma14)]
- External data: Stellar velocity dispersion sigma_e = 266 ± 13 km/s  
  > "The galaxy has a stellar velocity dispersion at the effective radius of $\sigma_e = 266 \pm 13$ km s$^{-1}$" (1.1 The galaxy NGC 7052) [from (cite: Gultekin09; Veale18)]
- External data: Previous MBH (2.5±0.3)e9 Msun from higher-resolution ALMA  
  > "yielded a refined $M_{\rm BH}$ $=(2.5\pm0.3)\times10^9$ M$_{\odot}$ (cite: Smith21)" (1.1 The galaxy NGC 7052) [from (cite: Smith21)]

## Processing

### Calibration

- pipeline or manual: Calibrated with CASA version provided by ALMA archive; bandpass J2253+1608, phase J2115+2933  
  > "We calibrated the data using the COMMON ASTRONOMY SOFTWARE APPLICATION (CASA[^3]) package (cite: McMullin07), version 6.5.2.26, provided by the ALMA Science Archive[^4]." (2 ALMA observation and reduction)
- casa version: 6.5.2.26  
  > "version 6.5.2.26, provided by the ALMA Science Archive" (2 ALMA observation and reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: continuum self-calibration applied to line SPW  
  > "After applying the continuum self-calibration to the line SPW" (2.2 CO emission imaging)

### Imaging

- task: tclean (MFS for continuum)  
  > "We used the `tclean` task in multifrequency synthesis mode (cite: Rau11) to generate the continuum image" (2.1 Continuum emission)
- deconvolver: Högbom  
  > "The final data product was generated using a Högbom deconvolver (cite: Hogbom74)" (2 ALMA observation and reduction)
- weighting robust: Briggs, robust = 0.5  
  > "We adopted Briggs weighting with a robust parameter of 0.5" (2.1 Continuum emission)
- uv taper: _not stated_
- cell size: 0.079"  
  > "a 128 $\times$ 128 pixel$^2$ image with a pixel scale of $0.079\ensuremath{''}$" (2 ALMA observation and reduction)
- image size: 128 x 128 pixels  
  > "a 128 $\times$ 128 pixel$^2$ image with a pixel scale of $0.079\ensuremath{''}$" (2 ALMA observation and reduction)
- masking: interactive cleaning in emission regions, threshold 1.5 x RMS  
  > "cleaned interactively in regions of emission with a threshold of 1.5 times the RMS noise" (2.2 CO emission imaging)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, linear fits to line-free channels  
  > "using the CASA `uvcontsub`, which forms a continuum model from linear fits to line-free channels in frequency" (2.2 CO emission imaging)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.31" x 0.23" (CO cube)  
  > "Mean synthesised beam ($''$$^2$)                 | 0.31 $\times$ 0.23" (Table 2)
- final rms: 0.5 mJy/beam per 10 km/s channel  
  > "Sensitivity (mJy beam$^{-1}$ per 10 km s$^{-1}$) |                0.5" (Table 2)

### Inherited from earlier work

- MGE stellar model procedure followed from Smith21  
  > "following the same procedure as (cite: Smith21)" (3.2 Our improved stellar-mass model) [from (cite: Smith21)]
- CO(2-1)/CO(1-0) flux ratio of unity  
  > "We also adopt a flux density ratio of unity between $^{12}$CO($2-1$) and $^{12}$CO($1-0$) (cite: Smith21)." (2.3 moment maps) [from (cite: Smith21)]
- Noise rescaling by (2N)^0.25 for covariance  
  > "The idea was originally proposed by (cite: vandenBosch09), later adapted by (cite: Mitzkus17)" (4.3 Bayesian inference and priors) [from (cite: vandenBosch09; Mitzkus17)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for uvcontsub
- Self-calibration solution intervals and number of rounds
- Cleaning niter/threshold details and exact tclean parameters
- Rest-frame velocity convention details and exact cube channel start
- Exact MGE fit settings and masks
- SkySampler/KinMS settings beyond those given (e.g. initial guesses)
- The continuum flux in text (29.1 mJy) differs from Table 1 (24.9 mJy)

## Analysis recipe

1. **Image continuum and CO cube**: tclean Briggs robust 0.5; continuum MFS from continuum SPWs and line-free channels; uvcontsub then 10 km/s cube  
  > "We then created the $^{12}$CO(2$-$1) data cube using the `tclean` task with Briggs weighting parameter of 0.5 and adopted a channel width of 10 km s$^{-1}$" (2.2 CO emission imaging)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Moment maps, spectrum and PVD**: masked moment method with smoothed-cube mask, threshold 0.5 sigma in unsmoothed cube  
  > "These maps were generated directly from the $^{12}$CO(2$-$1) data cube using the masked moment method (cite: Dame11)." (2.3 moment maps)
   - fitting: _not stated_
   - validation: _not stated_
3. **Molecular gas mass**: M_gas from integrated CO flux 45 Jy km/s with XCO  
  > "We estimated the total molecular gas mass using the “CO-to-H$_2$ conversion factor” of $X_{\rm CO} = 2 \times 10^{20}{\rm cm^{-2}(K\,km~s^{-1})^{-1}}$ (cite: Bolatto2013)" (2.3 moment maps)
   - assumption: XCO = 2e20, CO(2-1)/CO(1-0) = 1, D_L = 69.3 Mpc  
  > "We also adopt a flux density ratio of unity between $^{12}$CO($2-1$) and $^{12}$CO($1-0$) (cite: Smith21)." (2.3 moment maps)
   - fitting: _not stated_
   - validation: compared with Nobeyama single-dish mass  
  > "but is consistent with the previously estimated mass of $2.3 \times 10^9$ M$_{\odot}$ derived from $^{12}$CO(1$-$0) emission using the Nobeyama 45-m single-dish telescope" (2.3 moment maps)
4. **Stellar mass model from HST**: PSF (TinyTim) deconvolved, masked MGE fit of WFC F814W sky-subtracted image  
  > "we first decomposed the PSF into an MGE, which was then used as input for the subsequent MGE fit of the F814W masked and sky-subtracted image" (3.2 Our improved stellar-mass model)
   - software: MgeFit, TinyTim, Drizzlepac/AstroDrizzle, SExtractor
   - assumption: constant M/L, no dark matter in the center  
  > "by assuming a constant *M/L* (taken from its best-fit constrained in Section [4.4](#sec:results)) and ignoring the contribution of dark matter in the central region" (3.2 Our improved stellar-mass model)
   - fitting: MGE fit  
  > "we first decomposed the PSF into an MGE, which was then used as input for the subsequent MGE fit of the F814W masked and sky-subtracted image" (Our improved stellar-mass model)
   - validation: compared with Smith21 MGE  
  > "For a sanity check, we compared our derived stellar mass model with the one from (cite: Smith21)" (3.2 Our improved stellar-mass model)
5. **Gas mass MGE**: two single-Gaussian MGE fits to the CO mass map (one per peak), fixed in the mass model  
  > "we performed two separate MGE fits for the molecular gas mass and later combined the results." (3.3 Interstellar medium mass model)
   - software: MgeFit
   - fitting: _not stated_
   - validation: reconstructed map compared with data  
  > "It appears that our reconstructed molecular gas mass model describes the data well." (3.3 Interstellar medium mass model)
6. **Dynamical model fit of MBH and M/L**: KinMS forward-model of the 3D cube; gas distribution from SkySampler or two Gaussians; circular velocity from mge_circular_velocity; 9 free parameters  
  > "Thus, our adopted KINMS models consist of nine free parameters, as listed in Table [5](#tab:mcmc-results)." (4.1 KINMS tool)
   - software: KinMS, SkySampler, JamPy, AdaMet
   - parameter: 10^5 MCMC iterations, 20% burn-in; log-scale MBH; chi2 uncertainties rescaled by (2N)^0.25 with N=76,014  
  > "The MCMC chains consisted of $10^5$ iterations, with the initial 20% discarded as a burn-in phase." (4.3 Bayesian inference and priors)
   - assumption: circular orbits, thin disc, constant velocity dispersion, D = 69.3 Mpc  
  > "we assumed that the $^{12}$CO(2$-$1) gas circulates around the galaxy center in circular orbits" (4.1 KINMS tool)
   - fitting: Adaptive Metropolis MCMC (AdaMet), chi2 likelihood, uniform priors over ranges in Table 5  
  > "The adaptive Metropolis algorithm (cite: Haario01), implemented within a Bayesian framework using the ADAMET[^11] package (cite: Cappellari13a)" (4.3 Bayesian inference and priors)
   - validation: moment-map, PVD and spectrum comparisons, velocity residuals, minor-axis PVD, alternative models  
  > "Our best-fit KINMS model with SKYSAMPLER provides $|V_{\rm residual}| \lesssim 15$ km s$^{-1}$ ($\lesssim$4%) across the CND" (4.4 Results)
7. **Systematic error tests**: vary distance, disk thickness, dispersion profile, MGE masking, M/L(r) profiles  
  > "we discuss a variety additional sources of uncertainty in dynamical modeling" (4.5 Uncertainties)
   - software: KinMS
   - fitting: same MCMC  
  > "These new best-fitting KINMS models were run with the Bayesian method as described in Section [4.3](#sec:bayesian-infer)" (Mass model with M/L$_{\rm F814W}$ variations)
   - validation: _not stated_

## Software

- **CASA** 6.5.2.26: calibration, tclean, uvcontsub, imfit  
  > "version 6.5.2.26, provided by the ALMA Science Archive" (2 ALMA observation and reduction)
- **KinMS** : forward modelling of gas kinematics  
  > "we analyzed our ALMA gas kinematics using the publicly available PYTHON version of the KINEMATIC MOLECULAR SIMULATION tool" (4.1 KINMS tool)
- **SkySampler** : gas distribution from CLEAN components  
  > "we employed the SKYSAMPLER approach (cite: Smith19) to derive the CLEAN gas component directly from the ALMA data." (4.2.1 SKYSAMPLER)
- **AdaMet** 2.0: adaptive Metropolis MCMC  
  > "`AdaMet 2.0` (cite: Cappellari13a)" (Software)
- **MgeFit** 5.0: MGE fits to stellar light and gas  
  > "`MgeFit 5.0` (cite: Cappellari02)" (Software)
- **JamPy** 7.2: mge_circular_velocity  
  > "`JamPy 7.2` (cite: Cappellari20)" (Software)
- **TinyTim** 7.5: HST PSF model  
  > "we first generated the HST/WFPC2 WFC PSF for the F814W filter using the TINYTIM package" (3.2 Our improved stellar-mass model)
- **SExtractor** : point-source catalogue for masking  
  > "using a point-source catalogue generated by SEXTRACTOR[^9] (cite: Bertin96)" (3.2 Our improved stellar-mass model)
- **Drizzlepac/AstroDrizzle** : combine PSFs  
  > "resampled onto a final grid with a pixel size of $0.079\ensuremath{''}$ using `Drizzlepac`/ASTRODRIZZLE" (3.2 Our improved stellar-mass model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| MBH (SkySampler) | 2.50e9 | ±0.37e9 (stat), ±0.8e9 (sys) | Msun | 6 | $(2.50 \pm 0.37 \, [{\rm statistical}] \pm 0.8 \, [{\rm systematic}]) \times10^9$ M$_{\odot}$ |
| M/L F814W (SkySampler) | 4.08 | ±0.23 (stat), ±0.4 (sys) | Msun/Lsun | 6 | $4.08 \pm 0.23\, [{\rm statistical}] \pm 0.4 \, [{\rm systematic}]$ M$_{\odot}$/L$_\odot$$_{,I}$ |
| MBH (two Gaussians) | 2.34e9 | +0.39/-0.52 e9 | Msun | 6 | $M_{\rm BH}$ $=(2.34^{+0.39}_{-0.52})\times10^9$ M$_{\odot}$ |
| Total molecular gas mass | 2.2e9 | not stated | Msun | 3 | the total molecular gas mass is estimated to be $M_{\rm gas} \approx 2.2 \times 10^9$ M$_{\odot}$ |
| Inclination (SkySampler) | 73.49 | +0.42/-0.44 | deg | 6 | $i$ ($^\circ$)                            / 42 $\rightarrow$ 89.9    / 73.49      / +0.42,$-$0.44 |
| Position angle (SkySampler) | 63.90 | +0.50/-0.51 | deg | 6 | $\Gamma$ ($^\circ$)                       / 0 $\rightarrow$ 360      / 63.90      / +0.50,$-$0.51 |
| Reduced chi2 (SkySampler) | 0.867 | not stated | dimensionless | 6 | corresponding to a reduced chi-squared of $\chi^2_{\rm red, min} = 0.867$ |
| Radius of SOI | 152±24 pc (0.45") | ±24 pc | pc | 0 | we estimate $R_{\rm SOI}=152\pm24$ pc $\approx$ 0.45$''$$\pm$0.07$''$ |

## Qualitative findings

- Lower-resolution data still resolve the SOI and give MBH consistent with the earlier higher-resolution result; M/L is 10% lower owing to the improved mass model.  
  > "While our $M_{\rm BH}$ estimate is fully consistent with the previous determination, the $I$-band mass-to-light ratio is lower by 10%." (abstract)

## Claim tuples

- H: A 0.3" ALMA CO(2-1) cube can yield a reliable MBH in NGC 7052 | E: KinMS fits with SkySampler and Gaussian gas distributions | R: MBH = 2.50±0.37e9 Msun; Gaussian model gives 2.34e9 | F: Consistent with Smith21 despite 3x lower resolution | **supported**
- H: Wide-field stellar and molecular gas mass model changes M/L | E: MGE from HST WFC with PSF deconvolution plus gas MGE | R: M/L 4.08 vs 4.55 of Smith21 | F: M/L is 10% lower | **supported**
- H: Lower ionized-gas MBH is inconsistent with CO kinematics | E: Model with the lower MBH of Marel1998 fitted | R: cannot reproduce the central velocity rise | F: Ionized-gas value rejected | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Cold molecular gas less affected by turbulence and probes within the SOI  
  > "These tracers are less affected by turbulent motions (cite: Davis20) and allow us to probe deeply into the SOI" (Introduction)
- Alternative: Models with no SMBH and with MBH=4.5e9 fail to reproduce central rotation  
  > "These models match the extended kinematics of the CND but fail to reproduce the increase in rotation speed toward the center." (4.4 Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Distance uncertainty (69.3 vs 46.4 Mpc) gives ~30% systematic in MBH, dominant error  
  > "This discrepancy results in a systematic uncertainty of $\sim$30% in $M_{\rm BH}$" (4.5.1 Distances)
- Caveat (inferred, ours): Quoted systematic errors (0.8e9, 0.4) are only loosely derived from the tests
- Caveat (inferred, ours): Continuum flux inconsistent between text (29.1 mJy) and Table 1 (24.9 mJy)
- Caveat (inferred, ours): Conclusions list beam 0.31x0.23 while abstract gives 0.29x0.22
- Caveat (inferred, ours): Adopted noise rescaling (2N)^0.25 is ad hoc

## Reproducibility

- Data public (paper): ALMA archive data with project code; reduced with archive CASA version  
  > "version 6.5.2.26, provided by the ALMA Science Archive" (2 ALMA observation and reduction)
- Products in archive: _not stated_
- Missing: Line-free channels and self-calibration parameters
- Missing: Exact MGE fitting parameters/masks
- Missing: KinMS initial guesses and masks
- Missing: Archive vs. own-reduced data not clear
- Data volume (inferred): ~10-30 GB raw for one 12-m C-6 execution; final cube small (128x128)
- Score (inferred): 6/5, Public data and fairly complete modelling description with software named and tables of fits, but some imaging and self-cal details missing.
- Rediscovery candidate: yes, Public data, forward-model recipe largely described, numeric MBH and M/L results.

## Links

- Method: (cite: Davis13Nature) (KinMS)
- Method: (cite: Smith19) (SkySampler)
- Method: (cite: Cappellari13a) (AdaMet)
- Companion: (cite: Smith21) (Previous higher-resolution ALMA MBH of NGC 7052)
- Related: WISDOM
- Related: MBHBM*
- Related: MASSIVE survey

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 66,
  "rate": 0.759
 },
 "evidence_ok": true
}
```
