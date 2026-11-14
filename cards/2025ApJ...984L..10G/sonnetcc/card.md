# exoALMA. V. Gaseous Emission Surfaces and Temperature Structures

`2025ApJ...984L..10G` | The Astrophysical Journal Letters 2025 | first author: Galloway-Sprietsma, Maria | arXiv: 2504.19902 | DOI: 10.3847/2041-8213/adc437

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Where do 12CO J=3-2, 13CO J=3-2 and CS J=7-6 emit vertically in the 15 exoALMA disks, what 2-D (r-z) temperature structure and substructure do the surfaces and radial intensity profiles show, and how does emission height relate to disk properties such as disk mass  
  > "In this paper, we present the emission surfaces, intensity radial profiles, and two-dimensional temperature profiles of the fifteen sources." (1 Introduction); "this relationship offers a straightforward way to infer the disk mass." (abstract)
- Target **exoALMA sample of 15 protoplanetary disks**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2021.1.01123.L
- bands: _not stated_
- frequencies and spectral setup: Requested spectral resolution 35.5 kHz (26 m/s); surfaces extracted from 100 m/s cubes (12CO, 13CO) and 200 m/s cubes (CS)  
  > "a 35.5 kHz (26 m s$^{-1}$) spectral resolution" (2 Data); "the continuum-subtracted cubes with 200 m s$^{-1}$ resolution and 0.15$''$ beamsize for CS" (3.1 Non-Parametric Surfaces)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.1'' requested; images used 0.15'' (fiducial) and 0.30'' (high surface brightness sensitivity, used for DM Tau)  
  > "Observations of $^{12}$CO $J=3-2$, $^{13}$CO $J=3-2$, and CS $J=7-6$, at 0.1$''$ angular resolution" (2 Data); "the non-continuum subtracted cubes with 100 m/s resolution and 0.15$''$ beamsize for $^{12}$CO and $^{13}$CO" (3.1 Non-Parametric Surfaces); "where we use the 0.30$''$ beamsize cubes for both $^{12}$CO and $^{13}$CO surface extraction" (3.1 Non-Parametric Surfaces)
- max recoverable scale: _not stated_
- sensitivity: 3 K over 150 m/s requested  
  > "with a sensitivity of 3 K over 150 m s$^{-1}$ were requested to ensure a detection of line emission in the outer disk" (2 Data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated)
- Line: 13CO J=3-2 (not stated)
- Line: CS J=7-6 (not stated)
- External data: Geometric parameters (M*, i, PA, vLSR, x0, y0) derived with DISCMINER  
  > "We use geometric parameters (M$_{*}$, $i$, ${\rm PA}$, $v_{\rm LSR}$, x$_0$, y$_0$) derived from DISCMINER (see (cite: exoALMA_main; exoALMA_line_profiles))." (3.1 Non-Parametric Surfaces) [from (cite: exoALMA_main; exoALMA_line_profiles)]
- External data: Continuum temperatures T_cont used as lower bound on T_mid  
  > "The lower bounds of $T_{\rm mid}$ are set by the continuum temperatures $T_{\rm cont}$ derived in (cite: exoALMA_cont)." (4.3 2-D Temperature Structure) [from (cite: exoALMA_cont)]
- External data: Continuum rings and gaps used for comparison with surface substructure  
  > "We compare the emission surface substructure radial locations with the rings and gaps in the continuum reported by (cite: exoALMA_cont)." (5.3 Comparison with Dust Continuum) [from (cite: exoALMA_cont)]
- External data: Proposed planet locations (velocity kinks)  
  > "within a beamsize of the proposed planet locations listed in Table 2 of (cite: exoALMA_channel_maps)" (5.4 Comparison with Velocity Signatures) [from (cite: exoALMA_channel_maps)]
- External data: Disk masses from rotation curves and from dust mass  
  > "disk mass derived from the rotation curves in (cite: exoALMA_disk_mass) (left panel), disk mass derived from dust mass measurements from (cite: exoALMA_cont) (middle panel)" (6.1 Comparison with Source Properties) [from (cite: exoALMA_disk_mass); (cite: exoALMA_cont)]
- External data: Disk mass derived using N2H+  
  > "and disk mass derived using N$_2$H$^+$ from (cite: exoALMA_trapman) (rightmost panel)" (6.1 Comparison with Source Properties) [from (cite: exoALMA_trapman)]
- External data: Literature compilation of emission heights, stellar masses, disk sizes used as background sample  
  > "Here, we build off of the data compiled in (cite: law_2022ApJ...932..114L; law_2023ApJ...948...60L; paneque_2025arXiv250108294P), adding the exoALMA sources" (6.1 Comparison with Source Properties) [from (cite: law_2022ApJ...932..114L; law_2023ApJ...948...60L; paneque_2025arXiv250108294P)]
- Simulation/model as data: MCFOST simulated cubes (30 and 60 degree inclination, 12CO and 13CO J=3-2) used to compare disksurf and DISCMINER surfaces  
  > "The simulated cubes were made with MCFOST" (11 Comparing Disksurf to DISCMINER)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
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
- continuum subtraction: 12CO and 13CO surfaces and peak intensities from non-continuum-subtracted cubes; CS surfaces and all integrated intensities from continuum-subtracted cubes  
  > "We opt for the non-continuum subtracted cubes for $^{12}$CO and $^{13}$CO to ensure we retrieve accurate temperature measurements" (3.1 Non-Parametric Surfaces); "therefore, we opt to use the continuum subtracted cubes for the CS surfaces." (3.1 Non-Parametric Surfaces)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.15'' (fiducial, 100 m/s); 0.30'' high surface brightness sensitivity images used for DM Tau  
  > "the non-continuum subtracted cubes with 100 m/s resolution and 0.15$''$ beamsize for $^{12}$CO and $^{13}$CO" (3.1 Non-Parametric Surfaces); "where we use the 0.30$''$ beamsize cubes for both $^{12}$CO and $^{13}$CO surface extraction" (3.1 Non-Parametric Surfaces)
- final rms: _not stated_

### Inherited from earlier work

- Observations, source selection and imaging (calibration, cube production) described in the exoALMA overview and imaging papers  
  > "A complete description of observations, source selection, and imaging techniques used are described in (cite: exoALMA_main) and (cite: exoALMA_imaging)." (2 Data) [from (cite: exoALMA_main) and (cite: exoALMA_imaging)]
- Geometric parameters taken from the DISCMINER modelling of the exoALMA line profiles  
  > "We use geometric parameters (M$_{*}$, $i$, ${\rm PA}$, $v_{\rm LSR}$, x$_0$, y$_0$) derived from DISCMINER (see (cite: exoALMA_main; exoALMA_line_profiles))." (3.1 Non-Parametric Surfaces) [from (cite: exoALMA_main; exoALMA_line_profiles)]
- Non-parametric surface method (isovelocity-contour peak finding)  
  > "which utilizes the method outlined in (cite: pinte_2018A&A...609A..47P)" (3.1 Non-Parametric Surfaces) [from (cite: pinte_2018A&A...609A..47P)]
- Two-layer sinusoidal 2-D temperature model  
  > "we adopt the two-layer model connecting the atmosphere temperature to the midplane temperature with a sinusoidal equation originally used in (cite: dartois_2003A&A...399..773D)" (4.3 2-D Temperature Structure) [from (cite: dartois_2003A&A...399..773D)]
- Cumulative flux definition for the gas disk radius  
  > "(see Equation A.1 in (cite: sanchis_2020A&A...633A.114S))" (4.1 Gas Disk Size) [from (cite: sanchis_2020A&A...633A.114S)]
- Radial profile uncertainties from per-channel noise  
  > "We report uncertainties of the radial profiles which account for the noise in each channel as described in (cite: yen_2016ApJ...832..204Y)." (4.2 Brightness Temperatures) [from (cite: yen_2016ApJ...832..204Y)]
- Prior ranges for the temperature fit informed by earlier modelling  
  > "These priors were informed by previous observations of similar disks and modeling efforts" (4.3 2-D Temperature Structure) [from (cite: dartois_2003A&A...399..773D; zhang_2021ApJS..257....5Z; calahan_2021ApJS..257...17C; MAPS_emission_surfaces_2021ApJS..257....4L)]
- Surface density profile used to convert rotational disk mass to Sigma(100 au)  
  > "inferred based on the rotational disk masses assuming the surface density profile used in (cite: exoALMA_disk_mass)" (6.1 Comparison with Source Properties) [from (cite: exoALMA_disk_mass)]
- <z/r> and linear fits made consistent with earlier compilations  
  > "we use methods consistent with those used for the compiled background points." (6.1 Comparison with Source Properties) [from (cite: law_2022ApJ...932..114L; law_2023ApJ...948...60L)]

### Not stated but needed to reproduce (our reading)

- Calibration pipeline/CASA versions, flux calibrator and self-calibration details (all deferred to exoALMA overview and imaging papers)
- Exact exoALMA cube versions and file names (Fiducial vs High Surface Brightness Sensitivity) and where to obtain them in the VADP/archive
- DISCMINER geometric parameters per disk (M*, i, PA, vLSR, x0, y0) from the companion line-profile paper
- disksurf settings beyond those listed (smoothing, per-disk visual masks for noise and diffuse emission, front/back selection)
- Priors used for the tapered power-law surface fit with emcee
- Stellar luminosities used for T_irr
- CS and 13CO outer-disk masking choices and which disks use which iteration settings
- GoFish inputs: exact bin settings, velocity resolution used when shifting and stacking, and radial range
- Per-disk field-of-view used when computing cumulative flux and R_edge

## Analysis recipe

1. **Extract non-parametric emission surfaces**: disksurf isovelocity-contour peak finding with iterative surface refinement; front surfaces only; J1604 and HD 135344B excluded  
  > "This method relies on the asymmetry of the line emission above the disk midplane to infer an emission height" (3.1 Non-Parametric Surfaces); "We have excluded J1604 and HD 135344B from this analysis, as they are too face-on to reliably separate the front and back surfaces" (3.1 Non-Parametric Surfaces)
   - software: disksurf, DISCMINER
   - parameter: 5 iterations; maximum beamsize decreased from 2 beams to 1 beam; minimum SNR increased linearly from 1.0  
  > "We repeat the iteration five times for each surface, allowing us to decrease the maximum beamsize from 2 beams for the first iteration to 1 beam on the subsequent iterations" (3.1 Non-Parametric Surfaces)
   - parameter: Final SNR clips 5.0 (12CO), 3.5 (13CO), 3.0 (CS)  
  > "Therefore, the final SNR clips for the surfaces are 5.0 for $^{12}$CO, 3.5 for $^{13}$CO, and 3.0 for CS." (3.1 Non-Parametric Surfaces)
   - parameter: Points binned by a quarter of a beamsize  
  > "The points are binned by a quarter of a beamsize." (3.1 Non-Parametric Surfaces)
   - assumption: SNR per point is intensity divided by cube RMS; Keplerian rotation assumed by disksurf  
  > "The SNR for each point is measured as the intensity divided by the cube RMS." (3.1 Non-Parametric Surfaces); "assumes purely Keplerian rotation, whereas DISCMINER takes into account any velocity deviations during modeling" (11 Comparing Disksurf to DISCMINER)
   - fitting: _not stated_
   - validation: Per-disk visual checks against channel maps; iterative vs non-iterative surfaces compared  
  > "These steps were done on a per-disk basis, and were visually justified by looking at the channel maps with the detected points overlaid." (3.1 Non-Parametric Surfaces)
2. **Fit tapered power-law parametric surfaces**: Tapered power law z(r) fitted to the non-parametric points with disksurf MCMC, and independently via DISCMINER line-profile modelling  
  > "We assume a tapered power law analytic prescription as the surface model" (3.2 Parametric Fitting); "DISCMINER fits a Keplerian model to each channel" (3.2 Parametric Fitting)
   - software: disksurf, emcee, DISCMINER
   - parameter: Free parameters z0, psi, r_taper, q_taper; best fit = 50th percentile, errors 16th/84th percentiles  
  > "The best-fit surfaces represent the 50th percentile parameters from the posterior distributions, and the errors are obtained from the 16th and 84th percentiles." (3.2 Parametric Fitting)
   - fitting: emcee affine-invariant sampler, 256 walkers, 100 burn-in steps, 1000 steps; priors not stated  
  > "We employ 256 walkers, 100 burn-in steps, and 1000 steps to obtain a fit to the non-parametric surface data points." (3.2 Parametric Fitting)
   - validation: disksurf and DISCMINER parametric surfaces compared; broadly consistent  
  > "Despite the slight parametric differences, both surfaces are broadly consistent." (3.2 Parametric Fitting)
3. **Compute mean <z/r> per surface**: Average of binned surface points, cutting points past the surface peak and interior to one beamsize  
  > "by taking an average of the binned surface points" (3.3 Emission Surface Results); "We cut points past the peak of the emission surface, thus excluding those that belong to the tapered portion of the surfaces." (3.3 Emission Surface Results); "We additionally exclude any data interior to one beamsize" (3.3 Emission Surface Results)
   - fitting: _not stated_
   - validation: Value checked at a common radius of 125 au across disks  
  > "We have verified that the $\langle z / r \rangle$ value is consistent when measured at the same radial location in each disk (125 au)" (3.3 Emission Surface Results)
4. **Measure gas disk size R_edge and R_90**: Cumulative integrated-intensity profile of 12CO normalised by its maximum; R_edge is the first peak; R95, R90, R68 from flux percentiles  
  > "We then take a cumulative sum of the intensity" (4.1 Gas Disk Size); "by taking the 95th, 90th, and 68th percentiles of the total flux" (4.1 Gas Disk Size)
   - software: scipy
   - parameter: No outer cutoff radius; hand-selected field of view covering all emission plus a few arcsec of noise  
  > "we do not define an outer cutoff radius and instead rely on a hand-selected field-of-view that encompasses all the emission" (4.1 Gas Disk Size)
   - fitting: _not stated_
   - validation: Flux compared with exoALMA overview paper; broadly consistent  
  > "but our results are broadly consistent" (4.1 Gas Disk Size)
5. **Derive brightness-temperature radial profiles**: GoFish shifted-and-stacked radial profiles of integrated and peak intensity (full Planck function), plus brightness temperatures at each disksurf r-z point  
  > "to obtain the integrated and peak intensity radial profiles from the 3-D data cubes in Jy beam$^{-1}$ km s$^{-1}$ and K respectively, assuming the full Planck function" (4.2 Brightness Temperatures); "we opt to use the non-continuum subtracted cubes as to not underestimate the temperatures" (4.2 Brightness Temperatures)
   - software: GoFish, disksurf
   - parameter: Azimuthal bins of one quarter of the beam FWHM  
  > "azimuthally averaging radial bins that are binned by one-quarter of the FWHM of the synthesized beam" (4.2 Brightness Temperatures)
   - assumption: CO optically thick and in LTE so T_B equals gas temperature  
  > "If we assume that the CO lines are optically thick and in local thermodynamic equilibrium (LTE), we can assume that the measured brightness temperature $T_B$ is equal to the gas temperature." (4.3 2-D Temperature Structure)
   - fitting: _not stated_
   - validation: GoFish and disksurf temperatures agree; differences generally under 5 K; DISCMINER profiles also compared  
  > "Even so, these differences are slight and generally under 5 K." (4.2 Brightness Temperatures)
6. **Fit 2-D (r-z) temperature structure**: Two-layer model with power-law atmosphere and midplane temperatures joined by a cos^2 profile up to height z_q; six free parameters fitted to the non-parametric surface temperatures  
  > "we adopt the two-layer model connecting the atmosphere temperature to the midplane temperature with a sinusoidal equation originally used in (cite: dartois_2003A&A...399..773D)" (4.3 2-D Temperature Structure)
   - software: emcee
   - parameter: Points below 20 K discarded; all CS points excluded  
  > "we discard the data points with brightness temperatures below 20 K because those likely probe optically thin emission" (4.3 2-D Temperature Structure)
   - parameter: Bounded priors on T_atm,0, T_mid,0, q_atm, q_mid, z0, beta (given in paper); T_mid bounded by continuum/CMB temperature below and irradiation temperature above  
  > "We have constrained the parameter space with priors as follows:" (4.3 2-D Temperature Structure)
   - assumption: Broad priors; fit convergence depended on them  
  > "but the convergence of the fits was contingent on these priors being in place" (4.3 2-D Temperature Structure)
   - fitting: emcee, 256 walkers, 1000 steps, 100 burn-in; two rounds, second initialised from the first; 50th percentile with 16th/84th percentile errors  
  > "adopting 256 walkers, 1000 steps, and 100 burn-in steps" (4.3 2-D Temperature Structure); "We then use the results of this first fit to inform the initial guess of a second round with the same number of walkers, steps, and burn-in steps." (4.3 2-D Temperature Structure)
   - validation: Sinusoidal form chosen over hyperbolic tangent form as it better reproduced the data; statistical errors only  
  > "We find that the sinusoidal function described below best reproduces the observations and gives more reasonable estimates of the midplane temperatures" (4.3 2-D Temperature Structure); "These represent only the statistical errors and do not include systematic errors which can be larger than the statistical errors." (4.3 2-D Temperature Structure)
7. **Identify substructure in surfaces and peak-intensity profiles**: Savitzky-Golay smoothing and scipy find_peaks, with visual confirmation; compare locations with continuum rings/gaps and velocity-kink planet locations  
  > "smoothed with a Savitzky-Golay filter for visual clarity, with a window length of one arcsecond and a polynomial order of 2" (5.1 Emission Surface Substructures); "smoothed using a Savitzky-Golay filter with a window length of five and a polynomial order of 3" (5.2 Radial Peak Intensity Substructures)
   - software: scipy
   - parameter: Minimum width and separation at least the beamsize (0.15''), up to two beamsizes (0.3''); prominence scaled to the beamsize or larger (surfaces), 7 to 15 K (peak intensity)  
  > "we set the minimum width of each substructure and the minimum distance between substructures to be at least the beamsize" (5.1 Emission Surface Substructures)
   - fitting: _not stated_
   - validation: Visual confirmation; consistency between iterative and non-iterative surfaces  
  > "we visually confirm by eye the validity of the substructures" (5.1 Emission Surface Substructures)
8. **Correlate <z/r> with stellar and disk properties**: Spearman and Pearson coefficients; linmix linear fit to R_edge; emcee linear fits to disk mass and surface density  
  > "to fit a line to the data" (6.1 Comparison with Source Properties); "We use the Pearson correlation coefficient (PCC, or r$_p$) to quantify the linear correlation" (6.1 Comparison with Source Properties)
   - software: linmix, emcee
   - parameter: emcee linear fits with 100 walkers and 5000 iterations  
  > "to obtain these linear fits with 100 walkers and 5000 iterations" (6.1 Comparison with Source Properties)
   - assumption: Priors keep the model above zero; errors propagated from <z/r> and M_disk  
  > "This allows us to place priors such that the model cannot be below zero." (6.1 Comparison with Source Properties)
   - fitting: linmix (R_edge relation) and emcee (disk mass and surface density relations)  
  > "to obtain these linear fits with 100 walkers and 5000 iterations" (6.1 Comparison with Source Properties)
   - validation: Repeated at fixed 125 au radius; outlier HD 143006 removed to test sensitivity  
  > "With this point removed, the PCC becomes r$_p$ = 0.76." (6.1 Comparison with Source Properties)
9. **Benchmark disksurf against DISCMINER on MCFOST cubes**: Both codes applied to simulated 30 and 60 degree inclined disks in 12CO and 13CO and compared with the tau = 2/3 surface  
  > "The simulated cubes were made with MCFOST" (11 Comparing Disksurf to DISCMINER)
   - software: MCFOST, disksurf, DISCMINER
   - fitting: _not stated_
   - validation: Root cause of differences between the codes left unresolved  
  > "The root cause of the underlying differences between the surfaces, both for the real data and simulated cubes, is still unknown." (11 Comparing Disksurf to DISCMINER)

## Software

- **bettermoments** : Moment-eight peak intensity maps (quadratic method)  
  > "with the quadratic method and assuming the full Planck function." (2 Data)
- **disksurf** : Non-parametric emission surfaces and parametric surface MCMC fit  
  > "This method relies on the asymmetry of the line emission above the disk midplane to infer an emission height" (3.1 Non-Parametric Surfaces)
- **DISCMINER** : Geometric parameters and parametric emission surfaces via line-profile modelling  
  > "has been used to derive the geometric parameters for each exoALMA source" (3.2 Parametric Fitting)
- **emcee** : MCMC fits of tapered power-law surfaces, 2-D temperature structure and linear relations  
  > "We employ 256 walkers, 100 burn-in steps, and 1000 steps to obtain a fit to the non-parametric surface data points." (3.2 Parametric Fitting)
- **GoFish** : Shifted-and-stacked integrated and peak intensity radial profiles  
  > "This method shifts and stacks the spectra, utilizing the known rotation of the disk, to better resolve the line profile" (4.2 Brightness Temperatures)
- **scipy** : Peak finding for R_edge and for substructure identification (find_peaks)  
  > "This function finds maxima or minima in 1-D data sets by comparison of neighboring values." (5.1 Emission Surface Substructures)
- **linmix** : Linear fit of <z/r> versus R_edge  
  > "to fit a line to the data" (6.1 Comparison with Source Properties)
- **MCFOST** : Simulated cubes for the disksurf versus DISCMINER test  
  > "The simulated cubes were made with MCFOST" (11 Comparing Disksurf to DISCMINER)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Overall average <z/r> of 12CO emission surfaces | 0.28 | not stated | dimensionless | 3 | We find $\langle z / r \rangle$ values for $^{12}$CO emission ranging from $\sim$0.13 to $\sim$0.4, with an overall average $\langle z / r \rangle$ of 0.28. |
| Average <z/r> of 13CO emission surfaces | 0.16 | not stated | dimensionless | 3 | to 0.32, with an average of 0.16. |
| Average <z/r> of CS emission surfaces | 0.18 | not stated | dimensionless | 3 | The average $\langle z / r \rangle$ for CS is 0.18 |
| Mean 12CO brightness temperature at 100 au | ~40 | 7 K | K | 5 | The mean $^{12}$CO brightness temperature at 100 au across all disks is $\sim$40 K $\pm$ 7 K. |
| Mean atmospheric temperature at 100 au across all disks | 43.4 | not stated | K | 6 | with a mean atmospheric temperature (T$_{\rm atm}$) at 100 au across all disks of 43.4 K |
| Average midplane temperature at 100 au | 24 | not stated | K | 6 | The average midplane temperature at 100 au across the disk sample is 24 K. |
| Range of midplane temperatures | 13 (AA Tau) to 32 (HD 34282) | not stated | K | 6 | We find midplane temperatures ranging from 13 K (AA Tau) up to 32 K (HD 34282). |
| Fraction of disks with viable surfaces showing localized surface substructure | 76% | not stated | percent | 7 | We find evidence of localized substructures in 76% of disks with viable emission surfaces. |
| Spacing of LkCa 15 12CO peak-intensity wave pattern | ~175 | not stated | au | 7 | The wave patterns are spaced roughly 175 au apart. |
| Spearman coefficient, <z/r> versus stellar mass | -0.16 | not stated | dimensionless | 8 | we find r$_s$ = -0.16 |
| Pearson coefficient, <z/r> versus R_edge | 0.67 | not stated | dimensionless | 8 | We find a PCC of r$_p$ = 0.67, indicating a strong positive correlation. |
| Slope of <z/r> versus R_edge linear relation | 0.00033 | +0.000053/-0.000052 | per au | 8 | 0.00033$^{+0.000053}_{-0.000052}$ |
| Pearson coefficient, <z/r> versus rotation-curve disk mass | 0.64 | not stated | dimensionless | 8 | with a PCC of r$_p$ = 0.64 |
| Pearson coefficient, <z/r> versus gas surface density at 100 au | 0.75 | not stated | dimensionless | 8 | with a PCC of r$_p$ = 0.75, in agreement with the prediction |
| Disk mass versus <z/r> fit coefficients (intercept, slope) | M_disk/Msun = 0.020 + 0.26 <z/r> | intercept +0.047/-0.0056; slope +0.23/-0.089 | Msun | 8 | 0.020_{-0.0056}^{+0.047} + 0.26_{-0.089}^{+0.23} |

## Qualitative findings

- 12CO surface generally lies above 13CO, which lies above CS, but 13CO and CS surfaces overlap in AA Tau, J1615, LkCa 15, SY Cha and V4046 Sgr in the inner disk  
  > "We find that in most disks, the $^{12}$CO surface lies above that of the $^{13}$CO surface" (3.3 Emission Surface Results)
- V4046 Sgr surface gap at 174 au is attributed to projection effects rather than a physical gap  
  > "Therefore, we conclude that this gap is likely not physically real, but rather an effect caused by the projection of the disk" (6.4.1 Projection Effects)
- Diffuse outer emission in AA Tau, DM Tau, LkCa 15 and SY Cha may indicate photo-desorption even in low-FUV Taurus, but projection effects are not excluded  
  > "However, more work is needed to model these disks to determine if they are truly experiencing photo-desorption" (6.3 Diffuse Emission)

## Claim tuples

- H: Do 12CO, 13CO and CS J=3-2 / J=7-6 trace different vertical layers in the exoALMA disks? | E: Non-parametric surfaces with disksurf, binned and averaged to <z/r> per line | R: Mean <z/r> about 0.28 (12CO), 0.16 (13CO), 0.18 (CS) | F: 12CO traces the upper atmosphere, 13CO and CS lower layers | **supported**
- H: Is emission height related to disk mass and disk size? | E: Correlate <z/r> of 12CO with R_edge and with disk masses from rotation curves, dust and N2H+ | R: PCC 0.67 with R_edge; 0.64, 0.38 and 0.20 with the three disk mass estimates | F: <z/r> is positively correlated with disk mass and could be used to infer it | **supported**
- H: Can the 2-D temperature structure be derived from multiple tracers? | E: Fit a two-layer sinusoidal model to surface brightness temperatures with emcee | R: Mean T_atm about 43 K and mean T_mid about 24 K at 100 au | F: Midplane temperature is likely an upper bound and analytic models do not fully account for the structure | **partially**
- H: Do emission surfaces and intensity profiles show substructure coincident with continuum or kinematic features? | E: Peak finding on rolling surfaces and radial peak intensity profiles; comparison with continuum gaps and velocity kinks | R: Localized substructure in 76% of disks; continuum correlation only in AA Tau, J1615 and MWC 758 | F: Substructure is common and often co-located between tracers, but a link to continuum rings and gaps is not significant overall | **partially**

## Reasoning

- Why this data: exoALMA targets kinematic planet detection in 15 disks at high angular and spectral resolution  
  > "The ALMA Large Program exoALMA aims to detect plants forming in-situ at sub-millimeter wavelengths, utilizing kinematic planet-detection techniques." (1 Introduction)
- Why this method: Non-continuum-subtracted cubes used for 12CO and 13CO to retain accurate temperatures  
  > "We opt for the non-continuum subtracted cubes for $^{12}$CO and $^{13}$CO to ensure we retrieve accurate temperature measurements" (3.1 Non-Parametric Surfaces)
- Alternative: Hyperbolic tangent temperature form tested and rejected in favour of the sinusoidal form  
  > "We tested other functional forms, including the hyperbolic tangent function used in (cite: dullemond_2020A&A...633A.137D)" (4.3 2-D Temperature Structure)
- How they decided it was enough: _not stated_
- Limitation (authors): Temperature uncertainties are statistical only  
  > "These represent only the statistical errors and do not include systematic errors which can be larger than the statistical errors." (4.3 2-D Temperature Structure)
- Limitation (authors): Midplane temperature is an extrapolation informed by priors  
  > "Because there is no optically thick data at the midplane, this value is an extrapolation informed by the priors." (4.3 2-D Temperature Structure)
- Caveat (inferred, ours): Per-disk visual masking and manual removal of diffuse points make surfaces hard to reproduce exactly
- Caveat (inferred, ours): Sample is only 13 disks for surfaces and 6 for CS, so correlations (r about 0.2-0.7) have limited significance and no p-values are given
- Caveat (inferred, ours): Disk mass correlation partly relies on rotation-curve masses that use the emission surface as a prior
- Caveat (inferred, ours): Temperature fit depends strongly on priors and on excluding points below 20 K

## Reproducibility

- Data public (paper): Value-Added-Data-Product (VADP) publicly available  
  > "The data discussed in this paper is provided as a publicly available Value-Added-Data-Product (VADP)." (7 Conclusions)
- Products in archive: Surfaces, temperatures, radial profiles and substructure locations are in the VADP release  
  > "parametric surfaces, peak intensity radial profiles, integrated intensity radial profiles, and the radial locations of the surface and intensity modulations are all included in the VADP release." (7 Conclusions)
- Code: disksurf and DISCMINER are open-source python codes; this paper's own scripts are not stated as released  
  > "utilized two open-source python codes for the analysis of the emission surfaces" (10 Comparing Disksurf to DISCMINER)
- Missing: Calibration and imaging recipe (deferred to exoALMA overview and imaging papers)
- Missing: DISCMINER geometry per disk from a companion paper
- Missing: Priors for the parametric surface fit and per-disk masks
- Missing: Stellar luminosities and exact data-product file versions
- Data volume (inferred): Roughly 100-500 GB for 15 disks x 3 lines of imaged cubes (fiducial and high-sensitivity versions); VADP products are small
- Score (inferred): 3/5, Data and derived products are public and most fitting settings (emcee walkers, SNR clips, smoothing, peak-finding) are given with numeric results, but calibration/imaging, DISCMINER geometry, per-disk masks and some priors are deferred or unstated.
- Rediscovery candidate: yes, Public exoALMA data and VADP, an explicit surface and temperature recipe, and numeric results (mean <z/r>, T_atm, T_mid, correlations) allow an approximate redo, though per-disk visual masking limits exactness.

## Links

- Method: Teague, Benisty, Facchini, Fukagawa & Pinte 2025 (cite: exoALMA_main) (Observations, source selection and imaging)
- Method: Loomis & exoALMA 2025 (cite: exoALMA_imaging) (Imaging procedure and fiducial cubes)
- Method: Teague, Law, Huang & Meng 2021 (cite: disksurf_2021JOSS....6.3827T) (disksurf code)
- Method: Pinte et al. 2018 (cite: pinte_2018A&A...609A..47P) (Emission-surface method from isovelocity contours)
- Method: Izquierdo et al. 2021, 2023 (cite: discminer1_2021A&A...650A.179I; discminer2_2023A&A...674A.113I) (DISCMINER line-profile modelling)
- Method: Dartois, Dutrey & Guilloteau 2003 (cite: dartois_2003A&A...399..773D) (Two-layer temperature model)
- Companion: Izquierdo et al. 2025 (cite: exoALMA_line_profiles) (Geometric parameters and line-profile fits)
- Companion: Curone et al. 2025 (cite: exoALMA_cont) (Continuum rings, gaps and temperatures)
- Companion: Pinte, Ilee & Huang 2025 (cite: exoALMA_channel_maps) (Kinematic perturbations and proposed planet locations)
- Companion: Longarini et al. 2025 (cite: exoALMA_disk_mass) (Rotation-curve disk masses)
- Companion: Trapman, Longarini & Rosotti 2025 (cite: exoALMA_trapman) (N2H+ disk masses)
- Companion: Rosotti, Longarini & Paneque-Carreno 2025 (cite: exoALMA_interpret_height) (Predicted relation between emission height and disk mass)
- Related: exoALMA
- Related: MAPS (Law et al. 2021)

## Checks

```json
{
 "quotes": 119,
 "quotes_ok": 119,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 116,
  "stated": 77,
  "rate": 0.664
 },
 "evidence_ok": true
}
```
