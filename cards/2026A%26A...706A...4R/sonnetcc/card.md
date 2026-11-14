# Resolving the terrestrial planet-forming region of HD 172555 with ALMA: I. Post-impact dust distribution

`2026A&A...706A...4R` | Astronomy and Astrophysics 2026 | first author: Roumeliotis, Z. | arXiv: 2512.04154 | DOI: 10.1051/0004-6361/202557986

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: Where is the millimeter-grain dust from the giant impact around HD 172555 located radially and azimuthally (a few au), as resolved by new ALMA Band 7 continuum observations?  
  > "In order to better constrain the radial and azimuthal distribution of the impact-produced dust at a few au around HD 172555, we present follow-up high resolution 0.87 mm continuum observations with ALMA." (Introduction)
- Target **HD 172555**: coordinates _not stated_; z/distance 28.79 +/- 0.13 pc  
  > "at a distance of 28.79$\pm$0.13 pc from Earth (cite: gaia_collaboration_vizier_2022)" (Introduction); distance from Gaia (cite: gaia_collaboration_vizier_2022)  
  > "at a distance of 28.79$\pm$0.13 pc from Earth (cite: gaia_collaboration_vizier_2022)" (Introduction)

## Data provenance

- ALMA projects: 2022.1.00793.S
- bands: Band 7 (0.87 mm)  
  > "Observations were split between a lower and higher spectral setup covering different frequencies within Band 7 (0.87 mm)." (2 Observations)
- frequencies and spectral setup: Two setups, 4 spws each. Higher: 1.875 GHz wide spws centered at 343.2, 345.2, 355.2, 357.2 GHz, channel width 488.281 kHz. Lower: 1.875 GHz wide spws at 328.9, 330.9, 340.9 GHz plus one 2 GHz wide spw at 342.9 GHz, resolution 31.3 MHz  
  > "In the higher setup, all four of the spectral windows were 1.875 GHz wide, centered at 343.2, 345.2, 355.2, and 357.2 GHz, with a channel width of 488.281 kHz." (2 Observations); "In the lower setup, three of the spectral windows were 1.875 GHz wide, centered at 328.9, 330.9, and 340.9 GHz, and one spectral window was 2 GHz wide centered at 342.9 GHz, with a resolution of 31.3 MHz." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m array  
  > "All observations were carried out using Band 7 receivers and the 12-m array" (2 Observations)
- configurations: _not stated_
- baselines: 27.5 to 3637.7 m for each setup  
  > "with baselines ranging between 27.5 and 3637.7 m for each setup" (2 Observations)
- angular resolution: Natural weighting + 0.08" taper: 166x148 mas (4.8x4.3 au); Briggs robust 0.5: 84x73 mas (2.4x2.1 au)  
  > "which led to a beam of 166$\times$148 mas (4.8$\times$4.3 au at the distance of HD 172555)" (2 Observations); "obtaining a resolution of 84$\times$73 mas (2.4$\times$2.1 au)" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: RMS 10.4 uJy/beam (natural weighting, tapered); 11.3 uJy/beam (Briggs robust 0.5)  
  > "and an RMS noise level of 10.4" (2 Observations); "with an RMS noise level of 11.3" (2 Observations)
- time on source: 6.6 hours on-source total  
  > "We observed the HD 172555 system for a total of 6.6 hours on-source with ALMA" (2 Observations)
- observing dates: Lower setup: five days between 16 May and 3 June 2023; higher setup: four times between 3 and 4 June 2023  
  > "Observations in the lower spectral setup were taken on five separate days between 16 May and 3 June 2023, and observations in the higher spectral setup were taken at four times between 3 and 4 June 2023." (2 Observations)
- pi or archival as stated: Cycle 9 project 2022.1.00793.S, PI Matra (new observations)  
  > "during Cycle 9 through project 2022.1.00793.S (PI: Matrà)" (2 Observations)
- Line: CS J=7-6 (342.883 GHz)
- Line: 12CO J=3-2 (345.796 GHz)
- Line: HCN J=4-3 (354.505 GHz)
- Line: HCO+ J=4-3 (356.734 GHz)
- Line: C18O J=3-2 (329.331 GHz)
- Line: 13CO J=3-2 (330.588 GHz)
- Line: CN J=3-2 (340.248 GHz)
- Other facility **Multi-wavelength photometry (far-infrared to millimeter)**: Photometry combined with the ALMA fluxes to build the SED  
  > "We create a combined disk and star spectrum (hereafter SED) from available multi-wavelength photometry" (4.4 SED modeling)
- Other facility **Gaia**: Distance to HD 172555  
  > "at a distance of 28.79$\pm$0.13 pc from Earth (cite: gaia_collaboration_vizier_2022)" (Introduction)
- External data: Disk flux density at 1.3 mm after accounting for the stellar contribution: 0.09 +/- 0.03 mJy  
  > "(cite: schneiderman_carbon_2021) report $F_{\rm \nu}=0.09\pm 0.03$ mJy" (3 Results) [from (cite: schneiderman_carbon_2021)]
- External data: Inclination from earlier modeling used as Gaussian prior (mean 76.5, sd 8.2)  
  > "using the results from modeling the inclination done by (cite: engler_detection_2018)" (4.2 The visibility modeling process) [from (cite: engler_detection_2018)]
- External data: Size distribution slope of smaller grains from infrared observations, dn/da ~ a^-3.95 +/- 0.10  
  > "flatter than that found by (cite: lisse_abundant_2009) for smaller grains probed by infrared observations, $dn/da \propto a^{-3.95 \pm 0.10}$" (4.4 SED modeling) [from (cite: lisse_abundant_2009)]
- External data: Scattered-light disk geometry and number density converted to surface mass density for comparison with the mm dust  
  > "we converted from number density given by (cite: engler_detection_2018) to surface mass density using their assumed vertical density structure" (5.2 Radial distribution) [from (cite: engler_detection_2018)]
- External data: CO ring and 1.3 mm dust constraints from earlier ALMA Cycle 1 data (CO radius 7.4 au, width 3.4 au; dust mass 1.8e-4 Earth masses)  
  > "(cite: schneiderman_carbon_2021) find a millimeter dust mass of (1.8$\pm$0.6)$\times 10^{-4}$ M$_\oplus$ from the observed continuum emission" (5.1 Comparison to previous observations) [from (cite: schneiderman_carbon_2021)]
- Simulation/model as data: Two RADMC-3D disk models fit to the visibilities: an axisymmetric Gaussian radial surface density model and a power law model with inner and outer radii, plus a point-source star  
  > "we fit our visibilities using two models, each with two components: an axisymmetric dust disk, and the star modeled as a point source" (4.1 The physical model)

## Processing

### Calibration

- pipeline or manual: ALMA observatory pipeline calibration  
  > "Standard calibrations were applied to each visibility dataset by the ALMA observatory using its pipeline." (2 Observations)
- casa version: CASA 6.6.5  
  > "Data manipulation was carried out using the Common Astronomy Software Applications (CASA) software version 6.6.5" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: Pipeline-calibrated visibilities, then flagged for lines, averaged and concatenated by the authors; no astrometric realignment applied  
  > "We did not implement any astrometric realignment for each observation" (2 Observations); "We then concatenated all datasets for each spectral window to obtain a final calibrated and time- and frequency-averaged continuum visibility dataset for each spectral setup." (2 Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean, multi-frequency synthesis, both spectral setups imaged jointly  
  > "implemented through the tclean task" (2 Observations); "We carried out the continuum imaging in multi-frequency synthesis mode with Hogbom deconvolution" (2 Observations)
- deconvolver: Hogbom  
  > "We carried out the continuum imaging in multi-frequency synthesis mode with Hogbom deconvolution" (2 Observations)
- weighting robust: Natural weighting (with u-v taper); also Briggs robust = 0.5  
  > "We chose a natural weighting scheme with a u-v taper of 0.08" to achieve maximum surface brightness sensitivity" (2 Observations); "with a standard robust value of 0.5" (2 Observations)
- uv taper: 0.08 arcsec  
  > "We chose a natural weighting scheme with a u-v taper of 0.08" to achieve maximum surface brightness sensitivity" (2 Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Spectral lines flagged before averaging for the continuum analysis (no subtraction described)  
  > "we flagged the spectral lines, then time and frequency averaged the visibilities" (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Higher and lower spectral setups imaged jointly  
  > "We jointly imaged the higher and lower spectral setups in CASA" (2 Observations)
- smoothing: _not stated_
- final beam: 166x148 mas (natural weighting + 0.08" taper); 84x73 mas (Briggs 0.5)  
  > "which led to a beam of 166$\times$148 mas (4.8$\times$4.3 au at the distance of HD 172555)" (2 Observations); "obtaining a resolution of 84$\times$73 mas (2.4$\times$2.1 au)" (2 Observations)
- final rms: 10.4 uJy/beam (tapered natural); 11.3 uJy/beam (Briggs 0.5)  
  > "and an RMS noise level of 10.4" (2 Observations); "with an RMS noise level of 11.3" (2 Observations)

### Inherited from earlier work

- Disk-only continuum image made by increasing a minimum u-v cutoff and subtracting an unresolved stellar point source  
  > "we aim to create a disk-only continuum image using a procedure similar to (cite: matra_dust_2020)" (3 Results) [from (cite: matra_dust_2020)]
- Rescaling factor f applied to the observatory-delivered visibility weights  
  > "need to be rescaled by a factor common to all visibilities within a given dataset (cite: marino_gap_2018; matra_kuiper_2019)" (4.2 The visibility modeling process) [from (cite: marino_gap_2018; matra_kuiper_2019)]
- Inclination Gaussian prior taken from earlier scattered-light modeling  
  > "using the results from modeling the inclination done by (cite: engler_detection_2018)" (4.2 The visibility modeling process) [from (cite: engler_detection_2018)]
- SED fitting with stellar model plus modified blackbody  
  > "using the methodology from (cite: yelverton_statistically_2019)" (4.4 SED modeling) [from (cite: yelverton_statistically_2019)]
- Relation between SED millimeter slope and grain size distribution slope q  
  > "uses an analytical formula derived by (cite: draineSubmillimeterOpacityProtoplanetary2006)" (4.4 SED modeling) [from (cite: draineSubmillimeterOpacityProtoplanetary2006)]
- Dust mass equation  
  > "we calculate a dust mass using the dust mass equation from (cite: hildebrand_determination_1983)" (5.1 Comparison to previous observations) [from (cite: hildebrand_determination_1983)]
- Relation between debris radial width and impactor mass  
  > "From (cite: schneiderman_carbon_2021), the expected mass of the impacting planet in M$_\oplus$ is" (5.3 Mass of the largest impacting planet); "Following from (cite: jackson_debris_2014), the radial width of the debris from a giant impact is directly related to the velocity dispersion of the debris." (5.3 Mass of the largest impacting planet) [from (cite: schneiderman_carbon_2021); (cite: jackson_debris_2014)]

### Not stated but needed to reproduce (our reading)

- Which channels were flagged as line-affected in each of the 8 spectral windows (exact line-free channel ranges for the continuum)
- Flux, bandpass and phase calibrators and the flux-scale uncertainty adopted
- Whether any self-calibration was applied
- tclean image size, cell size, mask, threshold/niter and primary beam correction
- imview region used to measure disk flux densities (visually defined, not given)
- Prior ranges for all free parameters (only the inclination prior is given)
- RADMC-3D setup: grain opacity, number of photon packages, image pixel size and grid, wavelength, stellar properties other than 7.7 Lsun
- GALARIO settings (image size, pixel scale) and initial walker positions for emcee
- Source and values of the stellar mass (1.76 Msun) and luminosity (7.7 Lsun)
- The photometry table and alpha_Pl frequencies used for the SED slope and q derivation
- How the star subtraction fit (Table 1) was sampled and its priors

## Analysis recipe

1. **Prepare continuum visibilities and image**: Line-flagged visibilities time and frequency averaged per spw, concatenated per setup, then imaged jointly with tclean  
  > "time and frequency averaged the visibilities (to 30 seconds and 1.875 GHz, the size of the entire spectral window, respectively)" (2 Observations); "We jointly imaged the higher and lower spectral setups in CASA using the CLEAN algorithm" (2 Observations)
   - software: CASA 6.6.5, tclean
   - parameter: Averaging to 30 s and 1.875 GHz; natural weighting with 0.08" u-v taper; also Briggs robust 0.5  
  > "time and frequency averaged the visibilities (to 30 seconds and 1.875 GHz, the size of the entire spectral window, respectively)" (2 Observations); "We chose a natural weighting scheme with a u-v taper of 0.08" to achieve maximum surface brightness sensitivity" (2 Observations)
   - assumption: No astrometric realignment needed since proper motion and parallax motion is small  
  > "We did not implement any astrometric realignment for each observation" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Subtract the star to make a disk-only image**: Iteratively image long-baseline visibilities with increasing minimum u-v cutoff to isolate the point-source star; fit star flux and position per setup; subtract the best-fit model visibilities from all baselines; image the residual  
  > "assuming the star is an unresolved point source, we fit the visibilities of the longest baselines with the above u-v cutoffs, now unbiased by any disk emission, to obtain a best-fit stellar flux and RA/Dec position" (3 Results); "We then subtract the best-fit model visibilities for each spectral setup from the entire visibility dataset for that setup, including all baselines, effectively subtracting the star from our data." (3 Results)
   - software: CASA 6.6.5, tclean
   - parameter: Minimum u-v distance 600 klambda (lower setup) and 700 klambda (higher setup), chosen visually  
  > "We find the best compromise to be a minimum u-v distance of 600 k$\lambda$ for the lower spectral setup and 700 k$\lambda$ for the higher spectral setup." (3 Results)
   - assumption: Star is a point source with constant amplitude on long baselines  
  > "we assume the star is a point source and appears with constant amplitude on long baselines" (3 Results)
   - fitting: _not stated_
   - validation: Stellar fluxes from the two setups are consistent within errors  
  > "We note that the fluxes are consistent within the errors, which include both random noise and flux calibration uncertainty." (3 Results)
3. **Measure disk flux density from images**: Flux measured in a visually defined region on the disk-only images made separately per setup and jointly  
  > "Using the CASA task imview and visually defining a region around the disk, we measure the flux density from images created separately from the visibilities from each spectral setup" (3 Results)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with the 1.3 mm flux from earlier ALMA data and the SED slope; consistent within 2 sigma  
  > "the emission we observe is consistent with the expected emission within 2$\sigma$" (3 Results)
4. **Fit visibilities with disk models**: RADMC-3D model image of the disk, Fourier transformed and sampled at the data u-v points with GALARIO, star added as point source, joint fit of both setups with emcee  
  > "to obtain a Fourier transform of the model image from RADMC-3D and sample it at the same u-v locations as the data from the higher and lower spectral setups" (4.2 The visibility modeling process); "implemented through the EMCEE v3.1.6 software package" (4.2 The visibility modeling process)
   - software: RADMC-3D, GALARIO, emcee v3.1.6
   - parameter: 110 walkers, 10000 steps, burn-in of 400 steps discarded  
  > "using 110 walkers (10 times the number of free parameters), and for 10000 steps" (4.2 The visibility modeling process); "after discarding the burn-in phase of 400 steps" (4.3 Visibility modeling results)
   - parameter: Vertical aspect ratio fixed at 0.05; free parameters include i, PA, R and Delta R (Gaussian) or R_in, R_out, p (power law), disk and star fluxes per setup, RA/Dec offsets, weight rescaling f  
  > "The vertical density distribution is again modeled as a Gaussian with a constant aspect ratio of 0.05." (4.1 The physical model)
   - assumption: Grains act as blackbodies around a 7.7 Lsun star, T proportional to r^-1/2  
  > "we set the radial temperature dependence by assuming the grains act as blackbodies around a star of 7.7 L$_\odot$, with the temperature proportional to $r^{-1/2}$" (4.1 The physical model)
   - assumption: Disk optically thin  
  > "low enough values to ensure the disk is optically thin, as is expected" (4.1 The physical model)
   - fitting: emcee affine-invariant MCMC; likelihood proportional to exp(-chi2_total/2) summed over the two setups; uniform priors on all parameters, plus a Gaussian prior on inclination (mean 76.5, sd 8.2)  
  > "The likelihood function is proportional to $e^{-\chi_{\rm total}^2/2}$, where $\chi_{\rm total}^2$ is the sum of the two $\chi^2$ from the fits to the higher and lower setups." (4.2 The visibility modeling process); "we placed a Gaussian prior, with a mean of 76.5and standard deviation of 8.2, only on the inclination" (4.2 The visibility modeling process)
   - validation: Visual convergence of chains checked  
  > "We ensured visual convergence of the MCMC chains" (4.2 The visibility modeling process)
5. **Assess goodness of fit with residual images**: Best-fit model visibilities imaged and subtracted from data visibilities; residual dirty images made with the same imaging parameters  
  > "We then produced a joint residual dirty image (right column in Fig. [2](#fig:data model residuals)) using the same imaging parameters as the data." (4.3 Visibility modeling results)
   - software: RADMC-3D, CASA
   - fitting: _not stated_
   - validation: No significant residuals; the data cannot distinguish the two models  
  > "indicating that both models are a good fit to the ALMA data and that our data cannot distinguish between the two models" (4.3 Visibility modeling results)
6. **SED modeling and grain size distribution slope**: SED from multi-wavelength photometry fitted with stellar model plus modified blackbody; millimeter slope converted to size distribution slope q  
  > "fitted it with a stellar model plus a modified blackbody model" (4.4 SED modeling); "which constrains the millimeter spectral slope to $2.74 \pm 0.03$" (4.4 SED modeling)
   - parameter: beta_s = 1.8 +/- 0.2 for astronomical silicates  
  > "which is taken to be $1.8 \pm 0.2$ for astronomical silicates" (4.4 SED modeling)
   - assumption: Disk dominated by grains smaller than the wavelength of the observation  
  > "which assumes that the disk is dominated by grains smaller than the wavelength of the observation" (4.4 SED modeling)
   - fitting: _not stated_
   - validation: ALMA flux densities within 2 sigma of SED expectation; q consistent with steady-state collisional models  
  > "Our ALMA flux densities in each spectral setup are within 2$\sigma$ of the expected values from the SED" (4.4 SED modeling); "we find $q=3.41\pm 0.05$, which is consistent with steady state collisional models" (4.4 SED modeling)
7. **Derive millimeter dust mass**: Dust mass equation with blackbody temperature at the model peak radius and scaled opacity  
  > "Using an equilibrium blackbody temperature of 213 K at 4.7 au, the median peak surface density radius found in the Gaussian model" (5.1 Comparison to previous observations)
   - parameter: T = 213 K at 4.7 au (Gaussian), 191 K at 5.9 au (power law)  
  > "If we instead use an equilibrium blackbody temperature of 191 K at 5.9 au" (5.1 Comparison to previous observations)
   - assumption: Opacity 10 cm^2/g at 1000 GHz scaled as nu^beta with beta=1, as in the earlier ALMA study; millimeter grains act as blackbodies  
  > "a dust grain opacity of 10 cm^2^ g^-1^ at 1000 GHz and scaling the dust grain opacity as $\kappa \propto \nu^\beta$ with $\beta=1$" (5.1 Comparison to previous observations); "we assume the millimeter grains we observe act as blackbodies" (5.1 Comparison to previous observations)
   - fitting: _not stated_
   - validation: Gaussian-model and power-law-model masses consistent with each other  
  > "which is consistent with the dust mass calculated from Gaussian model parameters" (5.1 Comparison to previous observations)
8. **Estimate largest impactor mass**: Scaling relation between impactor mass and disk radius and width, evaluated on randomly sampled MCMC (R, Delta R) pairs or (R_in, R_out) pairs  
  > "randomly sampled $R$, $\Delta R$ pairs from the Gaussian model MCMC samples" (5.3 Mass of the largest impacting planet); "we take $R$ to be the mean of the $R_{\rm in}$ and $R_{\rm out}$ and $\Delta R$ to be the difference between $R_{\rm out}$ and $R_{\rm in}$" (5.3 Mass of the largest impacting planet)
   - parameter: M_* = 1.76 Msun, planet bulk density 5.5 g/cm3  
  > "Using $M_*$ = 1.76M$_\odot$, $\rho_{\rm p}$ = 5.5 g cm$^{-3}$" (5.3 Mass of the largest impacting planet)
   - assumption: Gas has not affected the dynamics of the millimeter and larger grains since the impact  
  > "assuming gas has not impacted the dynamics of the millimeter and larger sized grains throughout the post-impact evolution" (5.3 Mass of the largest impacting planet)
   - fitting: _not stated_
   - validation: Compared with detection limits from direct imaging and radial velocity; large uncertainties prevent firm conclusions  
  > "the currently large uncertainties, particularly on the mass derived using the results from the Gaussian model, prevent us from drawing firm conclusions" (5.3 Mass of the largest impacting planet)
9. **Limit azimuthal asymmetry**: Ratio of peak intensities on the SE and NW sides of the disk-only image, with detection requiring the ratio to exceed 1 by 3 sigma  
  > "we find that the ratio of the southeast intensity, $I_{\mathrm{\nu, SE}}$, to the northwest intensity, $I_{\mathrm{\nu, NW}}$, is 1.21$\pm$0.39" (5.4 Limits on potential asymmetry)
   - assumption: Asymmetry is in the plane of the sky  
  > "assuming the asymmetry is in the plane of the sky" (5.4 Limits on potential asymmetry)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.6.5: Data manipulation, flagging, averaging, concatenation, imaging and flux measurement (imview)  
  > "Data manipulation was carried out using the Common Astronomy Software Applications (CASA) software version 6.6.5" (2 Observations)
- **tclean** : Continuum CLEAN imaging  
  > "implemented through the tclean task" (2 Observations)
- **imview** : Defining a region and measuring disk flux density  
  > "Using the CASA task imview and visually defining a region around the disk" (3 Results)
- **RADMC-3D** : Radiative transfer model images of the disk at 0.87 mm  
  > "radiative transfer code to create an image of the disk at 0.87 mm" (4.2 The visibility modeling process)
- **GALARIO** : Fourier transform of model images and sampling at the data u-v points  
  > "to obtain a Fourier transform of the model image from RADMC-3D and sample it at the same u-v locations as the data" (4.2 The visibility modeling process)
- **emcee** v3.1.6: Affine-invariant MCMC ensemble sampling of the visibility model posteriors  
  > "implemented through the EMCEE v3.1.6 software package" (4.2 The visibility modeling process)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stellar flux, lower setup (star-only fit) | 0.10 | 0.03 | mJy | 2 | Stellar Flux (mJy) / $0.10\pm0.03$ / $0.07\pm0.03$ |
| Stellar flux, higher setup (star-only fit) | 0.07 | 0.03 | mJy | 2 | Stellar Flux (mJy) / $0.10\pm0.03$ / $0.07\pm0.03$ |
| Disk flux density, lower setup (0.89 mm, from images) | 0.26 | 0.04 | mJy | 3 | we find $F_{\rm \nu}=0.26\pm 0.04$ mJy and $F_{\rm \nu}=0.17\pm 0.03$ mJy, respectively |
| Disk flux density, higher setup (0.86 mm, from images) | 0.17 | 0.03 | mJy | 3 | we find $F_{\rm \nu}=0.26\pm 0.04$ mJy and $F_{\rm \nu}=0.17\pm 0.03$ mJy, respectively |
| Disk flux density, both setups imaged together | 0.18 | 0.02 | mJy | 3 | we measure $F_{\rm \nu}=0.18\pm 0.02$ mJy, where all quoted errors are 1$\sigma$ |
| Disk outer extent along PA | ~8.6 (about 0.3 arcsec) | not stated | au | 1 | which corresponds to $\sim$8.6 au from the central star at the distance of HD 172555 |
| Gaussian model: centroid radius R | 4.7 | +2.8/-2.4 | au | 4 | $R$ (au) / $4.7^{+2.8}_{-2.4}$ |
| Gaussian model: FWHM width Delta R | 12.9 | +4.8/-5.7 | au | 4 | $\Delta R$ (au) / $12.9^{+4.8}_{-5.7}$ |
| Power law model: inner radius R_in (mode) | 4.7 | +0.3/-2.1 | au | 4 | $R_{\rm in}$ (au) / – / $4.7^{+0.3}_{-2.1}$ |
| Power law model: outer radius R_out (mode) | 7.1 | +3.3/-1.7 | au | 4 | $R_{\rm out}$ (au) / – / $7.1^{+3.3}_{-1.7}$ |
| Power law model: exponent p | 0.0 | +7.9/-5.1 | dimensionless | 4 | $p$ / – / $0.0^{+7.9}_{-5.1}$ |
| Position angle, Gaussian model | 121.5 | +23.1/-18.7 | deg | 4 | PA (º) / $121.5^{+23.1}_{-18.7}$ / $123.3^{+25.0}_{-14.7}$ |
| Inclination, Gaussian model (with Gaussian prior) | 71.5 | +6.3/-6.4 | deg | 4 | $i$ (º) / $71.5^{+6.3}_{-6.4}$ / $71.9^{+6.8}_{-6.6}$ |
| Millimeter spectral slope | 2.74 | 0.03 | dimensionless | 6 | which constrains the millimeter spectral slope to $2.74 \pm 0.03$ |
| Grain size distribution slope q | 3.41 | 0.05 | dimensionless | 6 | we find $q=3.41\pm 0.05$, which is consistent with steady state collisional models |
| Dust mass (Gaussian model parameters, T=213 K) | 9.4e-5 | 1.1e-5 | Earth masses | 7 | we calculate a dust mass of (9.4$\pm$1.1)$\times 10^{-5}$ M$_\oplus$ |
| Dust mass (power law model parameters, T=191 K) | 10.5e-5 | 1.2e-5 | Earth masses | 7 | we calculate a dust mass of (10.5$\pm$1.2)$\times 10^{-5}$ M$_\oplus$ |
| Largest impactor mass from Gaussian model | 0.5 | +19.2/-0.4 | Jupiter masses | 8 | we derive a mass estimate of $0.5^{+19.2}_{-0.4}$ M$_{\rm Jup}$ |
| Largest impactor mass from power law model | 4.5 | +13.5/-3.3 | Earth masses | 8 | we derive an estimate of $4.5^{+13.5}_{-3.3}$ M$_{\oplus}$ |
| SE/NW peak intensity ratio | 1.21 | 0.39 | dimensionless | 9 | we find that the ratio of the southeast intensity, $I_{\mathrm{\nu, SE}}$, to the northwest intensity, $I_{\mathrm{\nu, NW}}$, is 1.21$\pm$0.39 |

## Qualitative findings

- Star and an inclined disk of millimeter dust are detected out to ~9 au and down to 2.3 au on-sky, with no significant asymmetry  
  > "with no significant asymmetry in the dust distribution" (abstract)
- The millimeter grains sit closer to the star than the small grains traced by scattered light  
  > "the millimeter grains are closer to the star than the smaller grains, potentially by a factor of two" (5.2 Radial distribution)

## Claim tuples

- H: Is the millimeter dust from the giant impact around HD 172555 detectable and resolved? | E: ALMA Band 7 12-m array continuum imaging with star subtraction | R: Disk detected out to ~8.6 au with the star separated; flux 0.18 +/- 0.02 mJy | F: First spatially resolved millimeter image of the post-impact dust | **supported**
- H: What is the radial distribution of the millimeter dust? | E: Gaussian and power law RADMC-3D models fit to visibilities with emcee | R: Gaussian R = 4.7 au, width 12.9 au; power law R_in 4.7 and R_out 7.1 au | F: Surface density most likely peaks around 5 au but the width is model-dependent at this S/N | **partially**
- H: Do the millimeter grains and small grains share the same radial distribution? | E: Compare model surface density with scattered-light profile | R: Millimeter grains are closer to the star, possibly by a factor of two with high uncertainty | F: Offset could result from radiation pressure plus gas drag if gas density is high enough | **partially**
- H: Is the millimeter grain size distribution consistent with collisional evolution and does it differ from micron grains? | E: SED fitting including the ALMA fluxes and conversion of the millimeter slope to q | R: Slope 2.74 +/- 0.03 giving q = 3.41 +/- 0.05, versus 3.95 for micron grains from the literature | F: A break in the grain size distribution, confirming the overabundance of small grains | **supported**
- H: Is there an azimuthal asymmetry in the millimeter dust? | E: Compare SE and NW peak intensities in the disk-only image | R: Ratio 1.21 +/- 0.39, consistent with 1 | F: No asymmetry detected, though one below 117% could be present | **supported**
- H: What mass was the largest impacting planet? | E: Scaling relation with R and Delta R samples from each model | R: 0.5 MJup (Gaussian) and 4.5 Mearth (power law) | F: Power law model gives a terrestrial-mass impactor that is physically preferable, but estimates remain highly uncertain | **partially**

## Reasoning

- Why this data: Follow-up high resolution 0.87 mm continuum observations to constrain the radial and azimuthal distribution of the impact dust; the earlier ALMA data were unresolved  
  > "because these observations were spatially unresolved, the spatial distribution of the millimeter grains remains unknown" (Introduction)
- Why this method: Visibility-space modeling to formally constrain radial structure and geometry  
  > "In order to formally constrain the radial structure and geometry of dust, we fit our visibilities using two models" (4.1 The physical model)
- Alternative: Gaussian vs power law radial models; the data cannot distinguish them, though the power law is argued to be physically preferable from the impactor mass  
  > "our data cannot distinguish between the two models" (4.3 Visibility modeling results); "This makes the power law model physically preferable to the Gaussian model." (5.3 Mass of the largest impacting planet)
- How they decided it was enough: Visual check of MCMC convergence  
  > "We ensured visual convergence of the MCMC chains" (4.2 The visibility modeling process)
- Limitation (authors): Radial width is model-dependent at the S/N of the data  
  > "while the width inferred remains model-dependent at the S/N of the data" (abstract)
- Limitation (authors): Retrieved surface density distributions depend on the assumed radial temperature profile  
  > "We note that the retrieved surface density distributions we will discuss are dependent on our choice of radial temperature profile." (4.1 The physical model)
- Caveat (inferred, ours): Parameter ranges of the uniform priors, RADMC-3D grain properties and line-free channel selection are not given, so the posterior cannot be reproduced exactly
- Caveat (inferred, ours): Inclination is prior-driven (Gaussian prior sd 8.2 deg) and the posterior is as broad as the prior, so geometry is essentially unconstrained
- Caveat (inferred, ours): Gaussian-model dust mass and impactor mass rely on a single assumed blackbody temperature and opacity law
- Caveat (inferred, ours): Star-subtraction u-v cutoffs were chosen by eye
- Caveat (inferred, ours): Offset to scattered-light grains is based on a model-dependent width

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Line-flagged channel ranges and calibrator details
- Missing: Prior ranges, RADMC-3D settings and walker initialisation
- Missing: Stellar mass and luminosity sources, SED photometry table
- Missing: imview flux regions
- Data volume (inferred): Roughly 100-300 GB raw for about 9 execution blocks of Band 7 12-m data with fine channels in the higher setup; tens of GB calibrated; the averaged continuum visibilities are small
- Score (inferred): 3/5, Project code and imaging settings (weighting, taper, robust, CASA version) are given, as are MCMC walker/step counts, software versions and tabulated posterior values; but priors ranges, RADMC-3D setup, line-flag channels and star-fit details are missing, so exact numbers need reconstruction.
- Rediscovery candidate: no, The paper does not state that the data are public and key modeling inputs (prior ranges, RADMC-3D setup, line-free channels) are not given, so the recipe is incomplete.

## Links

- Method: (cite: matra_dust_2020) (Procedure for creating a disk-only image by removing the stellar point source in the u-v plane)
- Method: (cite: tazzari_galario_2018) (GALARIO visibility sampling code)
- Method: (cite: yelverton_statistically_2019) (SED fitting methodology)
- Method: (cite: marino_gap_2018; matra_kuiper_2019) (Weight rescaling in visibility fitting)
- Companion: future companion paper (not cited by key) (In-depth analysis of the spectral lines: detection, kinematics and composition)
- Companion: (cite: schneiderman_carbon_2021) (Earlier unresolved ALMA 1.3 mm continuum and 12CO J=2-1 observations of HD 172555)

## Checks

```json
{
 "quotes": 140,
 "quotes_ok": 140,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 20,
 "numeric_problems": 0,
 "fill": {
  "facts": 111,
  "stated": 84,
  "rate": 0.757
 },
 "evidence_ok": true
}
```
