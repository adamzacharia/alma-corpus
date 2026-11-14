# Kinematic Analysis of z = 4.3 Galaxies in the SPT2349─56 Protocluster Core

`2024ApJ...977..161V` | The Astrophysical Journal 2024 | first author: Venkateshwaran, Aparna | arXiv: 2409.13823 | DOI: 10.3847/1538-4357/ad7bb4

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: How do galaxies in the SPT2349-56 protocluster core move: are they rotating discs, and what are their rotation velocities, velocity dispersions, disc stability and dynamical support in a protocluster environment?  
  > "This leaves a gap in our understanding of how galaxies behave in a turbulent and interactive environment like that of a protocluster core." (Introduction); "we classify six sources to be rotating discs in an actively star-forming protocluster environment" (abstract)
- Target **SPT2349-56 protocluster core (sources C1-C7, the seven FIR-brightest galaxies)**: coordinates not stated for the core as a whole; per-source morphological and kinematic centres are tabulated (J2000, e.g. 23:49:42.7 -56:38:19.4)  
  > "Among these, SPT2349$-$56 is the brightest un-lensed protocluster core discovered at $z = 4.303$." (Introduction); "Throughout the analysis, we use a $\Lambda$CDM cosmology with $h = 0.678$, $\Omega_\mathrm{m} = 0.308$, $\Omega_\Lambda = 0.692$" (Introduction); "23:49:42.7 $-$56:38:19.4" (Table 1 (physical parameters)); z/distance z = 4.303 (1 arcsec = 6.897 kpc)  
  > "Among these, SPT2349$-$56 is the brightest un-lensed protocluster core discovered at $z = 4.303$." (Introduction); "Throughout the analysis, we use a $\Lambda$CDM cosmology with $h = 0.678$, $\Omega_\mathrm{m} = 0.308$, $\Omega_\Lambda = 0.692$" (Introduction); "23:49:42.7 $-$56:38:19.4" (Table 1 (physical parameters)); distance from Planck 2016 LambdaCDM cosmology (cite: Planck_2016); z = 4.303 is the flux-weighted kinematic centre of the protocluster core  
  > "Among these, SPT2349$-$56 is the brightest un-lensed protocluster core discovered at $z = 4.303$." (Introduction); "Throughout the analysis, we use a $\Lambda$CDM cosmology with $h = 0.678$, $\Omega_\mathrm{m} = 0.308$, $\Omega_\Lambda = 0.692$" (Introduction); "23:49:42.7 $-$56:38:19.4" (Table 1 (physical parameters))

## Data provenance

- ALMA projects: 2018.1.00058.S
- bands: Band 7  
  > "We use high-resolution ALMA Cycle 6 (2018.1.00058.S; PI: S. Chapman) Band 7 data" (2 Observations and data reduction)
- frequencies and spectral setup: Band 7 centred on the [CII] 158-um line; 6-point mosaic; cube channel width 13 km/s  
  > "We use high-resolution ALMA Cycle 6 (2018.1.00058.S; PI: S. Chapman) Band 7 data, centered on the \[CII\] 158-$\ensuremath{\mu}m$ line." (2 Observations and data reduction); "The data were obtained as a 6-point mosaic over several days in November 2018" (2 Observations and data reduction); "It has a channel width of 13 km s$^{-1}$" (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 1.4 km  
  > "The array configurations had baselines between 15 m and 1.4 km." (2 Observations and data reduction)
- angular resolution: 0.225'' x 0.166'' (1.55 kpc x 1.14 kpc at z = 4.303)  
  > "The spectral cube has an angular resolution of $\theta_x \times \theta_y = 0.225\ensuremath{''} \times 0.166\ensuremath{''}$" (2 Observations and data reduction); "high-resolution (1.55 kpc spatial resolution at $z = 4.303$)" (abstract)
- max recoverable scale: _not stated_
- sensitivity: RMS noise 0.5 mJy/beam per 13 km/s channel in the cube  
  > "root mean square (RMS) noise $\sigma_\mathrm{[C\textsc{ii}]} = 0.5$ mJy beam$^{-1}$" (2 Observations and data reduction)
- time on source: 35 to 57 minutes for each observation  
  > "with a total on-source integration time of 35 to 57 minutes for each observation" (2 Observations and data reduction)
- observing dates: several days in November 2018  
  > "The data were obtained as a 6-point mosaic over several days in November 2018" (2 Observations and data reduction)
- pi or archival as stated: ALMA Cycle 6, project 2018.1.00058.S, PI S. Chapman  
  > "ALMA Cycle 6 (2018.1.00058.S; PI: S. Chapman)" (2 Observations and data reduction)
- Line: C+ ([CII]) 158-um fine-structure line (2P3/2 -> 2P1/2), redshifted (not stated)
- External data: Observation details of the same data set, source naming convention and the list of FIR-brightest sources (Table 3)  
  > "See Table 1 in (cite: Hill_2020) for more details about the observations." (2 Observations and data reduction); "the seven FIR brightest sources listed in Table 3 of (cite: Hill_2020)" (4 Results) [from (cite: Hill_2020)]
- External data: Half-light radii of the individual sources, used to set the disc scale height z0  
  > "of the half-light radius of the individual sources (see (cite: Hill_2020) for values)" (3.2 Kinematic fitting) [from (cite: Hill_2020)]
- External data: Gas fractions f_gas per source  
  > "Gas fraction, as presented in (cite: Rotermund_2021)." (Table 3 notes) [from (cite: Rotermund_2021)]
- External data: alpha_CII = 7.3 +/- 1.2 Msun/Lsun (atomic gas mass to [CII] luminosity ratio)  
  > "Here we use values presented in (cite: Rizzo_2020), where $\alpha_{\mathrm{CII}} = 7.3 \pm 1.2$ $M_\ensuremath{\odot}/L_\ensuremath{\odot}$." (5.2 Toomre parameter analysis) [from (cite: Rizzo_2020)]
- External data: Dividing plane between discs and mergers in PVsplit parameter space  
  > "$-0.63P_{\mathrm{major}} - 0.27P_{\mathrm{V}} + 2.78P_{\mathrm{R}} - 2.72 = 0$ (cite: Roman_Oliviera_2023)" (5.3 PVsplit) [from (cite: Roman_Oliviera_2023)]
- External data: V/sigma values of comparison samples at other redshifts (Table of comparison samples, from studies using 3D kinematic modelling and an ionized tracer)  
  > "The studies chosen depend on two criteria - (i) It uses 3D kinematic modeling methods, (ii) It uses an ionized tracer." (Table of comparison samples) [from (cite: Foerster_Schreiber_2009; Teodoro_2016; Rizzo_2020; Neeleman_2020; Fratenalli_2021; Rizzo_2021; Lelli_2021; Jones_2021; Posses_2023)]
- Simulation/model as data: TNG50 predicted V/sigma evolution with redshift (median 3 +/- 1.5 at z = 4.303) used as comparison  
  > "we find that the mean SPT2349$-$56 value ($4.5 \pm 0.2$) is greater than the median TNG50 value of $3\pm 1.5$ by one standard deviation" (5.1.4 Numerical and analytical studies)
- Simulation/model as data: Hayward and Hopkins analytic feedback model predicting sigma_disp from f_gas and V_c, tested with f_gas = 0.7 and with the Rotermund f_gas  
  > "This leaves us with predicted $\sigma_{\mathrm{disp}}$ values that are approximately 2–5 times higher than the derived values." (5.1.4 Numerical and analytical studies)

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

- task: CASA tclean; MFS continuum then spectral cube; cleaned to 0.55 mJy (1.4 x RMS of the dirty cube)  
  > "They were concatenated and imaged using the `tclean` task, first using the multi-frequency synthesis (MFS) routine to obtain a continuum image" (2 Observations and data reduction); "The line cube was cleaned to a threshold of 0.55 mJy (1.4$\times$ the root-mean-square (RMS) noise in the dirty cube)" (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5 (compared robust -2 to 2)  
  > "We found that a robust value of 0.5 optimally balanced resolution and sensitivity." (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: imcontsub task on the cube  
  > "Applying the same weighting parameters, we construct a spectral cube, and subtract the continuum using the `imcontsub` task." (2 Observations and data reduction)
- line free channels: channels without [CII] emission (ranges not stated)  
  > "to obtain a continuum image using channels without \[CII\] emission" (2 Observations and data reduction)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.225'' x 0.166''  
  > "The spectral cube has an angular resolution of $\theta_x \times \theta_y = 0.225\ensuremath{''} \times 0.166\ensuremath{''}$" (2 Observations and data reduction)
- final rms: 0.5 mJy/beam per channel  
  > "root mean square (RMS) noise $\sigma_\mathrm{[C\textsc{ii}]} = 0.5$ mJy beam$^{-1}$" (2 Observations and data reduction)

### Inherited from earlier work

- Further observing details of the data set  
  > "See Table 1 in (cite: Hill_2020) for more details about the observations." (2 Observations and data reduction) [from (cite: Hill_2020)]
- Source naming convention (C1-C23)  
  > "Using the same naming convention presented in (cite: Hill_2020)" (3.1 Source detection) [from (cite: Hill_2020)]
- Half-light radii used for the scale height z0  
  > "of the half-light radius of the individual sources (see (cite: Hill_2020) for values)" (3.2 Kinematic fitting) [from (cite: Hill_2020)]
- Normalization options and other 3DBarolo details  
  > "(see (cite: 3db_2015) for more details)" (3.2 Kinematic fitting) [from (cite: 3db_2015)]
- Criteria for a rotation-supported system  
  > "a series of criteria exist in the literature (cite: Foerster_Schreiber_2018; Wisnioski_2019; Foerster_schreiber_2020; Jones_2021)" (5.1.1 Rotators vs. Mergers) [from (cite: Foerster_Schreiber_2018; Wisnioski_2019; Foerster_schreiber_2020; Jones_2021)]
- Kinematic misalignment angle definition  
  > "if we use the definition for kinematic misalignment angle ($\phi_{\mathrm{mis}}$) from (cite: Franx_1991)" (5.1.1 Rotators vs. Mergers) [from (cite: Franx_1991)]
- Hot (pressure-supported) vs cold (rotation-supported) V/sigma threshold of 3  
  > "We use the (cite: Burkert_2010) definition, where a galaxy is dynamically hot or pressure-supported if $V/\sigma \le 3$, and dynamically cold or rotation-supported if $V/\sigma > 3$." (5.1.2 Gas kinematics) [from (cite: Burkert_2010)]
- L_CII computed by replacing the CO line with [CII] in Eq. 1  
  > "$L_{\mathrm{CII}}$ is found via replacing the CO line luminosity calculations with the \[CII\] line in Eq. 1 of (cite: Solomon_1997)" (5.2 Toomre parameter analysis) [from (cite: Solomon_1997)]
- PVsplit parameters P_major, P_V, P_R from Eqns. 6, 7, 8  
  > "Applying Eqns. 6, 7 and 8 in (cite: Rizzo_2022) to our $p-v$ maps" (5.3 PVsplit) [from (cite: Rizzo_2022)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the calibration was manual or the archive pipeline; flux calibrator and flux-scale uncertainty (only phase and band-pass calibrators are named)
- Which execution blocks and array configurations (12-m vs 7-m) were concatenated and any self-calibration
- tclean parameters beyond weighting: cell size, image size, deconvolver, masking, niter, mosaic gridder, primary-beam correction limit, spectral axis definition (start, width, rest-frame/LSRK)
- Line-free channel ranges for the continuum image and for imcontsub fitting order
- Exact sub-cube centres for each source and per-source SEARCH thresholds in physical units (the sigma values are given but the Jy thresholds in the parameter file are only for one case)
- 3DBarolo version and exact settings for the sigma_disp initial guesses and the (b/a) values from fitcomponents
- Per-source velocity-integrated [CII] fluxes, L_CII and the area/radius used for Sigma_gas and kappa in the Toomre Q calculation ('per unit area' is not defined)
- How the noise-weighted means and their quoted uncertainties are computed (weights, error propagation), and why the abstract (sigma 43.5) and Table/Conclusion (48.4) differ
- How the Pearson correlation between Q_T and V/sigma was computed (sample size, whether C7 is included)

## Analysis recipe

1. **Image the continuum and the [CII] line cube**: Concatenate the data, run tclean with MFS to make a continuum image from line-free channels, then build a cube with the same Briggs weighting and subtract the continuum with imcontsub  
  > "They were concatenated and imaged using the `tclean` task, first using the multi-frequency synthesis (MFS) routine to obtain a continuum image" (2 Observations and data reduction); "Applying the same weighting parameters, we construct a spectral cube, and subtract the continuum using the `imcontsub` task." (2 Observations and data reduction)
   - software: CASA, tclean, imcontsub
   - parameter: Briggs robust = 0.5  
  > "We found that a robust value of 0.5 optimally balanced resolution and sensitivity." (2 Observations and data reduction)
   - parameter: clean threshold 0.55 mJy (1.4 x dirty-cube RMS)  
  > "The line cube was cleaned to a threshold of 0.55 mJy (1.4$\times$ the root-mean-square (RMS) noise in the dirty cube)" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: Clean threshold choice does not significantly change the [CII] morphology  
  > "we note that choice of this parameter does not have a significant impact on the resulting morphology of the \[CII\] maps" (2 Observations and data reduction)
2. **Build SNR cube and SNR moment-0 map**: Estimate noise per position from emission-free channels, divide each channel by the noise map, and sum consecutive channels with SNR > 2.5 (fixed 160 km/s window where no significant emission)  
  > "The noise at each position was estimated using the emission free channels." (2 Observations and data reduction); "The SNR moment-0 was computed by summing all consecutive channels with SNR $> 2.5$ for positions with significant emission" (2 Observations and data reduction)
   - software: CASA
   - parameter: SNR > 2.5 for summed channels  
  > "The SNR moment-0 was computed by summing all consecutive channels with SNR $> 2.5$ for positions with significant emission" (2 Observations and data reduction)
   - assumption: Noise is mainly a function of position and almost constant along the frequency axis  
  > "This approach is justified since the noise is mainly a function of position and almost constant along the frequency axis" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: Constancy of the noise along frequency verified at emission-free positions  
  > "(as verified at the emission free positions)" (2 Observations and data reduction)
3. **Detect sources and make masks with 3DBarolo SEARCH**: Extract 2'' x 2'' sub-cubes (3'' x 3'' for C1) with imsubimage, run SEARCH with clipping only (5 sigma, grown to 2.1 sigma, 2.5 sigma for C1)  
  > "The task detects sources in position-position-velocity space, creating a mask using a combination of smoothing and clipping." (3.1 Source detection); "Here, we use only the clipping options, identifying the sources at 5$\sigma_{\mathrm{[C\textsc{ii}]}}$ and growing them down to 2.1$\sigma_{\mathrm{[C\textsc{ii}]}}$ around the emission peaks for sources C2–C7, and 2.5$\sigma_{\mathrm{[C\textsc{ii}]}}$ for source C1." (3.1 Source detection)
   - software: CASA imsubimage, 3DBAROLO SEARCH
   - parameter: SEARCH keywords: SEARCHTYPE spatial, THRESHOLD 0.0025005, GROWTHTHRESHOLD 0.0010002, MINCHANNELS 5, MINPIX 1  
  > "| SEARCHTYPE | spatial |" (Appendix: SEARCH keywords)
   - fitting: _not stated_
   - validation: Sources C1-C11 and C13 detected; C12 and C14-C23 not detected because of lower sensitivity than Hill et al. 2020  
  > "Using these thresholds, sources C1–C11 and C13 are identified in the" (3.1 Source detection)
4. **Derive initial guesses for the 3D fit**: Take x0, y0, Vrot, Vsys from SEARCH (flux-weighted moment-0 centre, adjusted with moment-1 and p-v maps where not at the kinematic centre); phi from moment-1; i from the (b/a) axis ratio measured with fitcomponents; sigma_disp set arbitrarily  
  > "We provide initial guesses for $x_0$, $y_0$, $V_{\mathrm{rot}}$ and $V_{\mathrm{sys}}$ using the results from the `SEARCH` task." (3.2 Kinematic fitting); "Lastly, $\sigma_{\mathrm{disp}}$ is arbitrarily set at values between 30–150 km s$^{-1}$." (3.2 Kinematic fitting)
   - software: CASA imageanalysis fitcomponents, 3DBAROLO SEARCH
   - parameter: cos^2 i = ((b/a)^2 - q^2)/(1 - q^2) with q = 0.2; cos i = b/a for edge-on C1, C4, C5  
  > "$i$ is then estimated using $\cos^2 i = ((b/a)^2 - q^2) / (1-q^2)$, where $q = 0.2$ for a mildly thick disc." (3.2 Kinematic fitting); "for galaxies that appear edge-on (C1, C4, and C5), we use $\cos i = (b/a)$" (3.2 Kinematic fitting)
   - assumption: Intrinsic axis ratio q = 0.2 (mildly thick disc)  
  > "where $q = 0.2$ for a mildly thick disc." (3.2 Kinematic fitting)
   - fitting: _not stated_
   - validation: Inclination checked against a contour enclosing 20% of the peak moment-0 intensity  
  > "The estimated $i$ is also verified against a fraction-of-peak contour that encloses 20% of the peak moment-0 intensity" (3.2 Kinematic fitting)
5. **Fit 3D tilted-ring models with 3DFIT**: 3DFIT builds concentric-ring models, convolves with the beam, and chi-squared-minimises against the cube; two-stage fit with Bezier regularisation of geometry (phi, i) first, then kinematics; four free parameters per ring (Vrot, sigma_disp, phi, i); x0, y0, Vsys fixed  
  > "The model is then convolved with the beam, before performing a $\chi^2$–minimization between the observed line emission and the model." (3.2 Kinematic fitting); "$x_0$, $y_0$, and $V_{\mathrm{sys}}$ are kept constant throughout after verification using the ($p-v$) diagrams and the moment-1 map." (3.2 Kinematic fitting)
   - software: 3DBAROLO 3DFIT
   - parameter: RADSEP = sqrt(theta_x theta_y)/2 (RADSEP 0.0968 in parameter file), near-Nyquist sampling  
  > "we use `RADSEP` $= \sqrt{\theta_x \theta_y}/2$" (3.2 Kinematic fitting)
   - parameter: NORM = azimuthal; TWOSTAGE true; REGTYPE bezier; FREE vrot vdisp pa inc; MASK search  
  > "Here we choose azimuthal normalization." (3.2 Kinematic fitting); "| REGTYPE | bezier |" (Appendix: 3DFIT keywords)
   - assumption: Thin disc with scale height z0 = 1/10 of the half-light radius  
  > "We assume a thin-disc approximation and set the scale height $z_{0}$ to 1/10th of the half-light radius of the individual sources" (3.2 Kinematic fitting)
   - assumption: Radial velocity Vrad = 0  
  > "We also assume the large-scale radial motion of the gas is obscured in the high rotation velocities, and set the radial velocity $V_{\mathrm{rad}} = 0$." (3.2 Kinematic fitting)
   - fitting: Chi-squared minimisation in 3D; errors from MCMC sampling of the parameter space around the best fit (not statistical errors)  
  > "The errors are obtained via a Markov-Chain Monte Carlo (MCMC) sampling of the parameter space around the best-fit value." (4.3 Velocity profiles)
   - validation: Compared azimuthal and localized normalization; tested Vrad as a free parameter (no significant radial motion); compared with p-v diagrams, moment maps and residual maps  
  > "We compared the output from both cases and find no large-scale structures in the galaxies, but the azimuthal normalization presented a better fit to the geometry." (5 Discussion)
6. **Derive mean rotation velocity, dispersion and V/sigma per source and for the sample**: Noise-weighted mean of Vrot and sigma_disp over the rings beyond the beam size (r > 1.55 kpc); V/sigma uses Vrot = V_flat and sigma_disp = sigma_extended measured beyond 0.22''  
  > "we tabulate the noise-weighted mean rotation velocity and dispersion, calculated by excluding the data points falling within the beam size" (4.3 Velocity profiles); "The second definition is used for our sample, where we set $V_{\mathrm{rot}} = V_{\mathrm{flat}}$ and $\sigma_{\mathrm{disp}} = \sigma_{\mathrm{extended}}$" (5.1.2 Gas kinematics)
   - software: 3DBAROLO
   - parameter: Points within the beam size (< 1.55 kpc) excluded; at least three independent measurements per profile remain  
  > "We are then left with at least three independent measurements for each velocity and dispersion profile." (4.3 Velocity profiles)
   - fitting: _not stated_
   - validation: sigma_disp of all galaxies exceeds the 13 km/s velocity resolution  
  > "The estimated $\sigma_{\mathrm{disp}}$ for all the galaxies are greater than the velocity resolution of 13 km s$^{-1}$" (4.3 Velocity profiles)
7. **Classify rotators versus mergers with dynamical criteria**: Test five literature criteria: smooth velocity gradient, V/sigma > 3, coincident centres (< 0.22''), kinematic and morphological axes within 30 deg, centrally peaked dispersion; plus p-v symmetry and double-peaked spectra  
  > "Therefore, for condition 3, if the distance between the kinematic and morphological center (determined using simple geometry) is less than $\theta_x = 0.22\ensuremath{''}$, then we assume that the centers are spatially coincident." (5.1.1 Rotators vs. Mergers); "Has morphological and kinematic major axes separated by less than $30\ensuremath{^\circ}$." (5.1.1 Rotators vs. Mergers)
   - parameter: V/sigma > 3 for rotation support  
  > "Is rotation-supported and has $V/\sigma > 3$." (5.1.1 Rotators vs. Mergers)
   - fitting: _not stated_
   - validation: All sources except C7 meet the criteria; C7 is discarded as a probable major merger  
  > "The exception is source C7, which appears to be a major merger" (5.1.1 Rotators vs. Mergers)
8. **Compute Toomre Q for disc stability**: Q_T = sigma_disp kappa / (pi G Sigma_gas), with kappa = sqrt(2) Vrot/R and Sigma_gas from L_CII times alpha_CII per unit area; L_CII from the Solomon et al. 1997 relation with CO replaced by [CII]  
  > "The Toomre parameter ($Q_\mathrm{T}$) measures the stability of a disc against gravitational perturbations." (5.2 Toomre parameter analysis); "$L_{\mathrm{CII}}$ is found via replacing the CO line luminosity calculations with the \[CII\] line in Eq. 1 of (cite: Solomon_1997)" (5.2 Toomre parameter analysis)
   - parameter: alpha_CII = 7.3 +/- 1.2 Msun/Lsun  
  > "Here we use values presented in (cite: Rizzo_2020), where $\alpha_{\mathrm{CII}} = 7.3 \pm 1.2$ $M_\ensuremath{\odot}/L_\ensuremath{\odot}$." (5.2 Toomre parameter analysis)
   - assumption: alpha_CII from Rizzo et al. 2020; the literature range is 5-30  
  > "The $\alpha_{\mathrm{CII}}$ parameter takes a range of values between 5 – 30" (5.2 Toomre parameter analysis)
   - fitting: _not stated_
   - validation: Compared with Q_T of about 0.96 beyond 1 kpc in z about 4.2 studies; gas surface density identified as the largest uncertainty  
  > "The largest source of uncertainty is the gas surface density, which could be mitigated using sophisticated means of flux profile extraction in future works." (5.2 Toomre parameter analysis)
9. **Classify morpho-kinematics with PVsplit**: Compute P_major, P_V, P_R from the p-v maps (Eqns. 6, 7, 8 of Rizzo et al. 2022) and classify with the dividing plane -0.63 P_major - 0.27 P_V + 2.78 P_R - 2.72 = 0  
  > "Applying Eqns. 6, 7 and 8 in (cite: Rizzo_2022) to our $p-v$ maps" (5.3 PVsplit); "$-0.63P_{\mathrm{major}} - 0.27P_{\mathrm{V}} + 2.78P_{\mathrm{R}} - 2.72 = 0$ (cite: Roman_Oliviera_2023)" (5.3 PVsplit)
   - software: PVsplit
   - fitting: _not stated_
   - validation: Applied although the sample does not meet the SNR criterion of the method; compared with Figure 17 of Rizzo et al. 2022  
  > "Targets in our sample do not meet the criteria for SNR, but we nevertheless apply the method" (5.3 PVsplit)
10. **Compare with simulations, analytic models and literature samples; assess protocluster interaction timescales**: Compare V/sigma with TNG50 and with 3D-modelled ionized-tracer samples at other redshifts; test the Hayward and Hopkins sigma_disp prediction with f_gas = 0.7 and with Rotermund f_gas; estimate crossing and relaxation times of the core  
  > "we find that the predicted $\sigma_{\mathrm{disp}}$ values are between 0.5–3 times the derived values" (5.1.4 Numerical and analytical studies); "In a protocluster system that is around 1 Gyr old" (5.4 Rotating discs in a protocluster core)
   - assumption: V_c = V_gas in the Hayward model since stellar and dark matter velocity contributions are not available  
  > "Since we do not have stellar and dark matter velocity contributions on hand, we substitute $V_\mathrm{c} = V_\mathrm{gas}$" (5.1.4 Numerical and analytical studies)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data reduction, tclean imaging, imcontsub continuum subtraction, imsubimage sub-cubes, imageanalysis fitcomponents  
  > "The data were reduced using Common Astronomy Software Applications" (2 Observations and data reduction)
- **3DBAROLO (SEARCH and 3DFIT tasks)** : Source detection and 3D tilted-ring kinematic fitting of the [CII] cubes  
  > "Using the publicly available code" (abstract); "These sub-cubes are then processed with the `SEARCH` task" (3.1 Source detection)
- **PVsplit** : Classification of discs versus mergers from position-velocity maps  
  > "we utilize a newly developed tool, `PVsplit` (cite: Rizzo_2022)." (5.3 PVsplit)
- **Astropy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Weighted mean rotation velocity of the sample (abstract) | 357.1 | 114.7 | km/s | 6 | The weighted mean rotation velocity ($V_{\mathrm{rot}}$) and velocity dispersion ($\sigma_{\mathrm{disp}}$) for the sample are $357.1 \pm 114.7$ km s$^{-1}$ |
| Weighted mean velocity dispersion of the sample (abstract value; the Table and Conclusion give 48.4 +/- 23.5) | 43.5 | 23.5 | km/s | 6 | $43.5 \pm 23.5$ km s$^{-1}$; The mean intrinsic velocity dispersion of the sample is $48.4 \pm 23.5$ km s$^{-1}$ |
| Weighted mean V_rot/sigma_disp | 4.5 | 1.3 | dimensionless | 6 | with weighted mean $V_{\mathrm{rot}}/\sigma_{\mathrm{disp}} = 4.5 \pm 1.3$ |
| Mean V/sigma of the sample excluding C7 | 4.5 | 0.2 | dimensionless | 6 | The mean of the sample (excluding source C7) is $4.5 \pm 0.2$. |
| Mean Toomre parameter Q_T (abstract and table; Section 5.2 gives 0.8 +/- 0.1, range 0.2-1.1) | 0.9 | 0.3 | dimensionless | 8 | find a mean Toomre parameter of $Q_\mathrm{T} = 0.9 \pm 0.3$; the mean value is $Q_\mathrm{T} = 0.8 \pm 0.1$, with individual values ranging from 0.2–1.1 |
| Pearson correlation between disc stability and V/sigma | about 0.19 | not stated | dimensionless | 8 | with a Pearson-$r$ coefficient of $\approx 0.19$ |
| Range of individual rotation velocities | 170-475 | not stated | km/s | 6 | individual values between 170–475 km s$^{-1}$ |
| Range of individual velocity dispersions | 10-100 | not stated | km/s | 6 | individual values between 10–100 km s$^{-1}$ |
| Mean derived inclination angle of the sample | about 60 | not stated | deg | 5 | The mean of the derived inclination angles for our sample is $\approx$ 60$^\circ$ |
| Cube RMS noise | 0.5 | not stated | mJy/beam | 1 | root mean square (RMS) noise $\sigma_\mathrm{[C\textsc{ii}]} = 0.5$ mJy beam$^{-1}$ |
| Synthesized beam of the cube | 0.225 x 0.166 | not stated | arcsec | 1 | The spectral cube has an angular resolution of $\theta_x \times \theta_y = 0.225\ensuremath{''} \times 0.166\ensuremath{''}$ |

## Qualitative findings

- Six of the seven FIR-brightest sources satisfy the dynamical criteria for rotating discs; C7 appears to be a major merger  
  > "we find evidence for six rotating discs and one possible major merger at $z = 4.303$ within a protocluster environment." (Conclusion)
- All sources show double-peaked spectra with varying asymmetry  
  > "We find double-peaked profiles with varying degrees of assymmetry across the systemic velocity for all the sources." (4.2 Moment maps and spectra)
- Sources C1 and C4 are stable rotating systems; the rest are unstable (Q_T < 1)  
  > "Sources C1 and C4 show rotation support with a stable disc, while the rest of the sources show rotation support with unstable discs." (5.2 Toomre parameter analysis)
- PVsplit places the sample in the disturbed-disc/merger region; only C3 is classified as a disc  
  > "we find that only source C3 identifies as a disc in our sample" (5.3 PVsplit)
- Sources C8-C11 and C13 are detected but too compact to model; C12 and C14-C23 are not detected  
  > "too few data points exist to properly model their kinematics" (4 Results)

## Claim tuples

- H: The FIR-brightest galaxies in the SPT2349-56 core are rotating discs | E: 3DBarolo 3D tilted-ring fits to [CII] cubes of C1-C7 and application of literature rotation-support criteria | R: Weighted mean Vrot = 357.1 +/- 114.7 km/s, sigma_disp about 44-48 km/s and V/sigma = 4.5 +/- 1.3; all but C7 satisfy the criteria | F: Six sources are rotating discs; C7 is a probable major merger | **supported**
- H: Discs in the core are dynamically stable and stability relates to rotational support | E: Toomre Q_T from [CII] luminosity, alpha_CII and the fitted rotation curves, compared with V/sigma | R: Mean Q_T = 0.9 +/- 0.3; only C1 and C4 are stable; Pearson r about 0.19 | F: Most discs are unstable; a mild positive correlation between stability and dynamical support | **partially**
- H: The morpho-kinematic nature from position-velocity maps agrees with the dynamical classification | E: PVsplit parameters P_major, P_V, P_R computed from p-v maps | R: All sources are disc-like in P_major and P_V; only C3 is a disc in P_R | F: Five sources are disturbed discs and one is a strict disc, so the sources are disturbed rotating discs | **supported**
- H: Rotating discs with high V/sigma can persist in an extreme protocluster environment | E: Compare V/sigma with TNG50 and field samples; estimate crossing and relaxation times of the core | R: Mean V/sigma of 4.5 exceeds the TNG50 median by one standard deviation; crossing and relaxation times are about 0.25-0.28 Gyr | F: Galaxies are likely disturbed by close interactions yet remain rotationally supported; whether this is typical remains open | **partially**

## Reasoning

- Why this data: Cycle 6 data alone chosen for longer baselines, prioritising spatial resolution over sensitivity  
  > "whereas we only use Cycle 6 data for its longer baseline, therefore prioritizing spatial resolution." (4 Results)
- Why this method: 3D modelling avoids deriving a velocity field and handles low SNR and low angular resolution  
  > "for its ability to handle low SNR data and low angular resolution data" (3 Methods)
- Alternative: Range of Briggs robust values from -2 to 2 compared; 0.5 chosen  
  > "We used the Briggs weighting mode and compared the results from a range of robust values between -2 and 2." (2 Observations and data reduction)
- Alternative: Localized versus azimuthal normalization compared; azimuthal gave a better geometric fit  
  > "We compared the output from both cases and find no large-scale structures in the galaxies, but the azimuthal normalization presented a better fit to the geometry." (5 Discussion)
- Alternative: Vrad left free: no significant large-scale radial motion  
  > "We also found there is no significant, large-scale radial motion present in the galaxies by setting the radial velocity as a free parameter" (5 Discussion)
- Alternative: Two-stage minimization preferred over user-supplied fixed angles  
  > "We find that this two-stage minimization process is efficient compared to user-supplied fixed angles." (5 Discussion)
- How they decided it was enough: Only C1-C7 modelled; C8-C11 and C13 too compact relative to the beam  
  > "we find that due to their spatial extent approaching the synthesized beam size, too few data points exist to properly model their kinematics." (4 Results)
- Limitation (authors): Thin-disc assumption may overestimate inclination (thick-disc comparison suggests about 7 deg lower)  
  > "there may be a possibility that we are overestimating the inclination angles" (5 Discussion)
- Limitation (authors): Rotating discs cannot be cleanly distinguished from compact mergers at this resolution  
  > "At the spatial resolution of our study, it remains difficult to distinguish between rotating discs and compact mergers." (5.1.1 Rotators vs. Mergers)
- Limitation (authors): MCMC errors are not statistical errors  
  > "We note here that the errors are not statistical errors, but a measure of how the well-behaved the parameter space is around the best-fit value" (4.3 Velocity profiles)
- Limitation (authors): PVsplit SNR criterion not met by the sample  
  > "Targets in our sample do not meet the criteria for SNR, but we nevertheless apply the method" (5.3 PVsplit)
- Limitation (authors): Gas surface density is the largest source of Q_T uncertainty  
  > "The largest source of uncertainty is the gas surface density" (5.2 Toomre parameter analysis)
- Limitation (authors): Lower sensitivity than Hill et al. 2020 so C12 and C14-C23 are not detected  
  > "Overall, this drop in sensitivity explains the lack of detection of the sources C12, and C14–C23." (4 Results)
- Caveat (inferred, ours): Internal inconsistencies: sample mean sigma_disp is 43.5 km/s in the abstract but 48.4 km/s in the Table and Conclusion; mean Q_T is 0.9 +/- 0.3 (abstract/table) but 0.8 +/- 0.1 in Section 5.2; V/sigma uncertainty is 1.3 (abstract) versus 0.2 (Section 5.1.3)
- Caveat (inferred, ours): The quoted +/- on weighted means (e.g. 114.7 km/s) looks like the sample scatter, not the error on the mean, and the weighting scheme is not defined
- Caveat (inferred, ours): Pearson r about 0.19 with n of 6-7 is not significant, so a 'mild positive correlation' is weakly supported
- Caveat (inferred, ours): Only about three independent rings beyond the beam per source; inner points are excluded, so the rotation curves rest on a few beam-sized elements
- Caveat (inferred, ours): Inclination from a morphological axis ratio with q = 0.2 and thin-disc models strongly drives Vrot (V/sin i) and V/sigma; no inclination uncertainty is propagated
- Caveat (inferred, ours): Toomre Q depends on an adopted alpha_CII (5-30 in the literature) and an ill-defined Sigma_gas area; no per-source L_CII or radii are tabulated
- Caveat (inferred, ours): Classification as disc versus merger relies on resolution of about 1.5 kpc and on PVsplit outside its SNR validity range
- Caveat (inferred, ours): Beam smearing and sigma_disp initial guess (30-150 km/s) sensitivity are not tested explicitly

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: 3DBarolo is publicly available and the SEARCH and 3DFIT parameter files are listed in the appendix  
  > "Using the publicly available code" (abstract); "show the sample parameter files used in the `SEARCH` and `3DFIT` tasks." (Appendix: Initial values and parameter file)
- Missing: CASA version, calibration route, flux calibrator and flux-scale uncertainty
- Missing: Full tclean parameters (cell, image size, mosaic gridder, deconvolver, mask, niter, spectral definition) and line-free channel ranges
- Missing: Per-source sub-cube centres and exact conversion of the sigma thresholds
- Missing: Per-source L_CII, fluxes, radii and area definition for Toomre Q; weights used for noise-weighted means
- Missing: Per-source table rows lost source labels in the text conversion
- Missing: Whether the ALMA data are public is not stated by the paper
- Data volume (inferred): Raw 6-pointing Band 7 mosaic over several execution blocks, likely tens to a couple hundred GB raw; the final cube and sub-cubes a few GB
- Score (inferred): 3/5, Project code, observing outline, key imaging choices (robust 0.5, 13 km/s channels, 0.55 mJy clean) and full 3DBarolo parameter files with initial guesses are given, and results are numeric; but CASA version, calibration, many tclean settings and the Toomre Q inputs are missing, and some headline numbers disagree between sections.
- Rediscovery candidate: yes, A single ALMA project code, a public fitting code with published parameter files and numeric headline results make a reasonable redo possible, though imaging details and the Toomre inputs must be inferred and the public status of the data is not stated by the paper.

## Links

- Method: (cite: 3db_2015) Di Teodoro & Fraternali 2015, MNRAS, 451, 3021 (3DBarolo method used for SEARCH and 3DFIT)
- Method: (cite: Rizzo_2022) (PVsplit method and equations 6-8 for morpho-kinematic classification)
- Method: (cite: Hill_2020) Hill et al. 2020, MNRAS, 495, 3124 (Observation details (Table 1), source names, half-light radii and the deeper Cycle 5+6 [CII] cube)
- Companion: (cite: Miller_2018) (ALMA Cycle 3 and 4 [CII] and CO(4-3) identification of 14 galaxies in the core)
- Companion: (cite: Rotermund_2021) (Gemini and Spitzer counterparts, stellar mass and gas fractions used in Table)
- Companion: (cite: Hill_2022) (HST and Spitzer observations showing galaxies lie on the main sequence)
- Companion: (cite: Rennehan_2020) (Hydrodynamical simulations of the core collapse and interactions)
- Related: South Pole Telescope 2500 deg2 survey
- Related: ALMA Cycle 6 project 2018.1.00058.S (PI S. Chapman)
- Related: ALMA Cycle 5 and 6 combined [CII] cube of Hill et al. 2020

## Checks

```json
{
 "quotes": 143,
 "quotes_ok": 143,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 126,
  "stated": 93,
  "rate": 0.738
 },
 "evidence_ok": true
}
```
