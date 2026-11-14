# exoALMA. XIV. Gas Surface Densities in the RX J1604.3−2130 A Disk from Pressure-broadened CO Line Wings

`2025ApJ...984L..19Y` | The Astrophysical Journal Letters 2025 | first author: Yoshida, Tomohiro C. | arXiv: 2504.19434 | DOI: 10.3847/2041-8213/adc42f

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What is the radial gas surface density and midplane pressure profile of the J1604 transition disk, derived from pressure-broadened CO J=3-2 line wings, and what does it imply for dust trapping, turbulence and planet formation?  
  > "Since pressure-broadened line wings are sensitive to the total gas volume density, we robustly constrain the radial dependence of the gas surface density and midplane pressure" (abstract)
- Target **RX J1604.3-2130 A (J1604)**: coordinates _not stated_; z/distance 144.6 pc  
  > "which is located at 144.6 pc from the Earth (cite: gaia23) in the Upper Scorpius star-forming region" (1 Introduction); distance from Gaia (cite: gaia23)  
  > "which is located at 144.6 pc from the Earth (cite: gaia23) in the Upper Scorpius star-forming region" (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00819.S, 2013.1.01020.S, 2015.1.00964.S, 2021.1.01123.L
- bands: Band 3 (3.1 mm), Band 6 (1.3 mm), Band 7 (0.9 mm continuum; CO J=3-2)  
  > "We use continuum images previously observed with ALMA at 1.3 mm (Band 6) and 3.1 mm (Band 3) in addition to the new exoALMA continuum image at 0.9 mm" (2.1 SED Modeling)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Band 3: 15 m to 331 m  
  > "The baseline lengths range from 15 m to 331 m, and the on-source integration time was 2.8 min." (Appendix: Data reduction of the Band 3 image)
- angular resolution: CO cube beam 0.15" circularized; channel width 0.1 km/s; Band 3 beam 2.7"x1.7"  
  > "The synthesized beam is circularized and has a full width at half maximum (FWHM) of $0.15\ensuremath{''}$. The channel width is set to $0.1\ {\rm km\ s^{-1}}$." (3.1 Stacked spectra)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Band 3: 2.8 min  
  > "the on-source integration time was 2.8 min" (Appendix: Data reduction of the Band 3 image)
- observing dates: Band 3: Jan. 20, 2016  
  > "The J1604 disk was observed on Jan. 20, 2016 in Band 3 with 41 antennas." (Appendix: Data reduction of the Band 3 image)
- pi or archival as stated: Band 3 archival (PI L. Ricci); exoALMA large program for CO; C18O archival  
  > "We newly analyze archival observations (# 2015.1.00819.S; PI L. Ricci) for the Band 3 image" (2.1 SED Modeling)
- Line: 12CO J=3-2 (not stated)
- Line: C18O J=2-1 (not stated)
- External data: Band 6 (1.3 mm) continuum image, beam 0.060"x0.039"  
  > "For Band 6, we use the image published by (cite: stad23), which has a beam size of $0.060\ensuremath{''} \times 0.039\ensuremath{''}$." (2.1 SED Modeling) [from (cite: stad23)]
- External data: Inclination fixed to 6.0 deg  
  > "The inclination angle is fixed to $i = 6.0\ensuremath{^\circ}$ (cite: stad23)." (3.1 Stacked spectra) [from (cite: stad23)]
- External data: Exoalma fiducial CO J=3-2 image cube  
  > "we use one of the fiducial exoALMA image cubes of the CO $J=3-2$ line (cite: Loomis_exoALMA)" (3.1 Stacked spectra) [from (cite: Loomis_exoALMA)]
- External data: Stellar mass 1.24 Msun and age ~5-10 Myr  
  > "with a mass of $M_\star = 1.24\ M_\odot$ and age of $\sim 5-10$ Myr (cite: mana20)" (1 Introduction) [from (cite: mana20)]
- External data: Spectroscopic constants (LAMDA) and broadening parameters (HITRAN)  
  > "we use the LAMDA database (cite: scho05; yang10) and HITRAN database (cite: HITRAN22; tan22), respectively." (3.2 Modeling the spectra) [from (cite: scho05; yang10; HITRAN22; tan22)]

## Processing

### Calibration

- pipeline or manual: Band 3: observatory calibration script (pipeline), then iterative self-calibration  
  > "We first ran the calibration script provided by the observatory using the Common Astronomical Software Application (cite: CASA) pipeline version 4.5.2." (Appendix: Data reduction of the Band 3 image)
- casa version: CASA 6.5.5 (modular) for remaining Band 3 analysis  
  > "CASA modular version 6.5.5 was used throughout the remaining analysis." (Appendix: Data reduction of the Band 3 image)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: Assumed 3x nominal: s_f = 0.075 (Band 3), 0.15 (Bands 6, 7)  
  > "substitute $s_f = [ 0.075, 0.15, 0.15 ]$ for Band 3, 6, and 7, respectively" (2.1 SED Modeling)
- self calibration: Band 3: three rounds of phase self-cal, solints = observation duration, 90 s, 30 s  
  > "Three rounds of phase self-calibration with solution intervals of the durations of the observation, 90s, and 30s were applied." (Appendix: Data reduction of the Band 3 image)

### Imaging

- task: CLEAN with MTMFS for Band 3  
  > "we adopted the MTMFS mode for CLEAN." (Appendix: Data reduction of the Band 3 image)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5 (Band 3; also C18O tclean)  
  > "The Briggs weighting with robust $=$0.5 was applied." (Appendix: Data reduction of the Band 3 image)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: C18O cube smoothed with imsmooth to 0.26"x0.26"; rms 8.8 mJy/beam per channel  
  > "We then smoothed the image cube with `imsmooth` and achieved a beam size of $0.26\ensuremath{''} \times 0.26\ensuremath{''}$." (Appendix: C18O)
- final beam: Band 3 2.7"x1.7"; images re-convolved to circular 2.7", 0.061", 0.14" (Bands 3, 6, 7)  
  > "The CLEAN images are re-convolved to have circularized beams of $2.7\ensuremath{''},\ 0.061\ensuremath{''}$, and $0.14\ensuremath{''}$, for Band 3, 6, and 7, respectively." (2.1 SED Modeling)
- final rms: Band 3: 0.05 mJy  
  > "The final RMS noise level is measured to be 0.05 mJy" (Appendix: Data reduction of the Band 3 image)

### Inherited from earlier work

- Pressure-broadened line wing (Voigt opacity) modeling approach  
  > "For the line opacity profile, we adopt the Voigt function and follow (cite: yosh22)." (3.2 Modeling the spectra) [from (cite: yosh22)]
- Vertical hydrostatic H2 density structure  
  > "is determined by assuming the vertical hydrostatic equilibrium self-consistent with the temperature structure (cite: Longarini_exoALMA)." (3.2 Modeling the spectra) [from (cite: Longarini_exoALMA)]
- Disk geometry for continuum model  
  > "we assume the geometry of the J1604 disk (cite: Curone_exoALMA)" (2.1 SED Modeling) [from (cite: Curone_exoALMA)]
- Dust radiative transfer approach  
  > "in the same manner as in recent similar studies (cite: sier21; maci21; guid22)" (2.1 SED Modeling) [from (cite: sier21; maci21; guid22)]

### Not stated but needed to reproduce (our reading)

- Exact exoALMA CO cube parameters (robust, taper, continuum subtraction) are only by reference to Loomis et al.
- Likelihood and noise definition for the CO spectral fit (per-channel noise estimate, fit velocity range) not specified
- Which radii/annuli spacing used for fits and how radial profiles are averaged/errors defined
- Band 7 continuum image details and absolute flux handling
- Details of Toomre Q computation (temperature, rotation) and gas-gap depth extrapolation
- Line-free channels and continuum subtraction for CO cube
- Details of exoALMA self-calibration for CO data

## Analysis recipe

1. **Multi-band dust SED modeling**: Parametric two-Gaussian ring dust surface density with power-law T, DSHARP opacity, self-scattering slab radiative transfer, fitted to Band 3, 6, 7 images  
  > "we assume that the dust surface density $\Sigma_d$ can be expressed by superposition of two Gaussian rings" (2.1 SED Modeling)
   - software: emcee, dsharp_opac
   - parameter: 8 free parameters; 5000 steps, 24 walkers; median from last 4200 steps  
  > "We adopt 5000 steps with 24 walkers for our MCMC chain. After confirming convergence, we calculate the median values from the last 4200 steps." (2.1 SED Modeling)
   - assumption: T_mid = T100 (r/100 au)^-0.5; grain size index -3.5; amin 1e-5 cm; DSHARP opacities  
  > "We set a grain size distribution as a power law with a fixed index of $-3.5$, and a flexible maximum grain size of $a_{\rm max}$." (2.1 SED Modeling)
   - fitting: emcee MCMC; chi2 with covariance C = sigma^2 delta + s_f^2 M_i M_j; two rounds (s_f=0 then nonzero)  
  > "In practice, we set $s_f = 0$ for all bands first and sampled the posterior probability distribution by the Markov-Chain Monte-Carlo (MCMC) method using `emcee`" (2.1 SED Modeling)
   - validation: Compared best-fit model with observations; residuals within flux uncertainties; tested slope -0.4  
  > "The relative difference between observations and models is almost within the flux uncertainties." (2.1 SED Modeling)
2. **Azimuthally stack CO spectra**: Velocity map from bettermoments, Keplerian fit with eddy for geometry, per-annulus fit of v_LOS vs azimuth, shift spectra and average over azimuth  
  > "The original spectra are then shifted by the derived line-of-sight velocities." (3.1 Stacked spectra)
   - software: bettermoments, eddy, eddy.linecube
   - parameter: annulus width 0.05"; i = 6.0 deg fixed  
  > "we pick up an annulus with a radial width of $0.05\ensuremath{''}$" (3.1 Stacked spectra)
   - assumption: Line wings identical along azimuth  
  > "When stacking the spectra, we make the assumption that the line wings are identical along the azimuthal direction." (3.1 Stacked spectra)
   - fitting: _not stated_
   - validation: Tested inclinations 1, 4, 8, 11 deg and quadrant stacking; no significant difference  
  > "As a result, no significant difference is observed, which means that our analysis is robust for the uncertainty in the geometrical parameters." (Appendix: CO line stacking)
3. **Test Gaussian broadening of wings**: Fit isothermal slab with Gaussian optical depth to |v|>0.8 km/s of averaged spectrum  
  > "We fitted the high-velocity range ($|v| > 0.8\ {\rm km\ s^{-1}}$) of the averaged spectrum by Equation ([\[eq:toymodel\]](#eq:toymodel)) using `scipy.optimize.curve_fit`" (3.1 Stacked spectra)
   - software: scipy.optimize.curve_fit
   - fitting: curve_fit; T ~ 4.8e3 K, tau0 ~ 1.9e-4 (unphysical)  
  > "The best-fit parameters are $T \simeq 4.8\times10^3\ {\rm K}$ and $\tau_{0} \simeq 1.9 \times10^{-4}$." (3.1 Stacked spectra)
   - validation: Wings ~ v^-2; fit deviates at large v; other mechanisms excluded  
  > "The wing emission at $|v| \gtrsim 1\ {\rm km\ s^{-1}}$ is almost proportional to $v^{-2}$." (3.1 Stacked spectra)
4. **Fit radial gas surface density with pressure-broadened line model**: Radiative transfer with Voigt opacity, layered vertical temperature, hydrostatic H2, continuum absorption; fit each radius  
  > "The convolved synthetic spectrum at each radius $r$ is then compared with the azimuthally stacked spectrum at the same radius." (3.2 Modeling the spectra)
   - software: emcee
   - parameter: 7 free parameters; T100 = 14 K fiducial and 30 K high case; X_CO = 1e-4; mu = 2.37  
  > "In our model fitting procedure, we fix $T_{\rm 100} = 14$ K as a fiducial case." (3.2 Modeling the spectra)
   - assumption: X_CO = 1e-4 tentatively; CO in gas phase at midplane; vertically constant X_CO  
  > "We tentatively assume $X_{\rm CO}=10^{-4}$ for fitting and discuss possible uncertainties in the following sections." (3.2 Modeling the spectra)
   - fitting: Uniform priors; 2000 steps x 32 walkers, then re-initialized 6000-step run discarding first 3000; median adopted  
  > "We re-run MCMC sampling for 6000 steps and check that the chains are well converged." (3.2 Modeling the spectra)
   - validation: Gaussian-opacity fit leaves significant wing residuals; factor-2 changes in Sigma_g fail to match wings  
  > "We confirm that the spectra cannot be well-fitted without pressure-broadening." (3.2 Modeling the spectra)
5. **Constrain X_CO and peak gas surface density via Toomre Q and literature range**: Require Q>1 at gas peak and combine with 1e-6<X_CO<1e-3  
  > "If we assume $Q > 1$ at the peak of the gas surface density, we can obtain $X_{\rm CO} > 7 \times 10^{-4}$." (4.1 Gas surface density profile)
   - assumption: Disk gravitationally stable (no spirals)  
  > "there is no significant asymmetric structure such as a spiral arm in the J1604 disk, suggesting the disk is gravitationally stable" (4.1 Gas surface density profile)
   - fitting: _not stated_
   - validation: _not stated_
6. **Estimate turbulence alpha and fragmentation velocity**: Steady-state advection-diffusion dust profile compared with observed dust ring width for three alpha; v_frag from St_max and alpha  
  > "When $\alpha_{\rm turb}$ is set to $2\times10^{-4}$, the observed width of the dust ring is well reproduced." (4.2 Turbulence and dust fragmentation)
   - parameter: a_rep = 0.6 mm from a_max = 1.4 mm; X_CO = 7e-4; alpha = 1e-3, 2e-4, 4e-5  
  > "We adopt $a_{\rm rep} = 0.6\ {\rm mm}$ by converting $a_{\rm max} = 1.4\ {\rm mm}$" (4.2 Turbulence and dust fragmentation)
   - fitting: _not stated_
   - validation: _not stated_
7. **C18O J=2-1 optical depth check**: Archival data pipeline-calibrated, combined, tclean cube, moment maps, peak brightness temperature with full Planck function  
  > "We combined the measurement sets to achieve higher sensitivity." (Appendix: C18O)
   - software: CASA, tclean, imsmooth, bettermoments
   - parameter: robust 0.5, channel 0.2 km/s, 4.0<v<5.2 km/s  
  > "using the CASA command `tclean` with the robust parameter of 0.5 and channel width of $0.2\ {\rm km\ s^{-1}}$" (Appendix: C18O)
   - fitting: _not stated_
   - validation: Compared with Bergner and MAPS integrated intensities  
  > "The peak brightness temperature exceeds $30$ K around the ring at $r \sim 80$ au and reaches $\sim35$ K at the peak." (Appendix: C18O)

## Software

- **CASA** pipeline 4.5.2; 6.5.5: Band 3 and C18O calibration, CLEAN, imsmooth  
  > "CASA modular version 6.5.5 was used throughout the remaining analysis." (Appendix: Data reduction of the Band 3 image)
- **emcee** : MCMC for continuum and CO spectral fits  
  > "using the MCMC method with `emcee` (cite: fore13)" (3.2 Modeling the spectra)
- **eddy** : Keplerian fit of velocity map and per-annulus fit  
  > "the velocity map is fitted by the geometrically thin Keplerian rotation model using `eddy` (cite: eddy)" (3.1 Stacked spectra)
- **bettermoments** : Line-of-sight velocity map and C18O moment maps  
  > "by fitting a tapered Gaussian with an optically thick core to the observed spectrum at each position using `bettermoments`" (3.1 Stacked spectra)
- **dsharp_opac** : Dust opacities  
  > "The dust opacities at each wavelength are calculated using `dsharp_opac`" (2.1 SED Modeling)
- **scipy.optimize.curve_fit** : Gaussian-broadening slab fit to wings  
  > "using `scipy.optimize.curve_fit`" (3.1 Stacked spectra)
- **astropy** : listed in Software section  
  > "astropy (cite: astropy:2013; astropy:2018), emcee (cite: fore13), eddy (cite: eddy)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak dust surface density | 0.35 | +0.03/-0.02 | g cm^-2 | 1 | The peak dust surface density is estimated to be $0.35^{+0.03}_{-0.02}\ {\rm g\ cm^{-2}}$ at a radius of $\simeq 82$ au |
| Maximum dust size a_max | 1.4 | +0.2/-0.1 | mm | 1 | The maximum dust size $a_{\rm amax}$ is estimated to be $1.4^{+0.2}_{-0.1}\ {\rm mm}$. |
| Total dust mass | 2.7e-4 | +0.2/-0.1 e-4 | Msun | 1 | we estimate a total dust mass of $2.7^{+0.2}_{-0.1}\times10^{-4}\ {M_\odot}$ |
| T100 from continuum | 14 | +1/-1 | K | 1 | $T_{100}$                 /     $14^{+1}_{-1}$      /        K |
| Peak gas surface density (fiducial T, X_CO=1e-4) | ~80 (X_CO/1e-4)^-0.5 | not stated | g cm^-2 | 4 | The maximum value at $r\sim87$ au is $\sim80 (X_{\rm CO}/10^{-4})^{-0.5}\ {\rm g\ cm^{-2}}$ |
| Peak gas surface density (conclusion) | 18-44 | not stated | g cm^-2 | 5 | we conclude the peak gas surface density of $18-44\ {\rm g\ cm^{-2}}$ with $1.6 \times 10^{-4} < X_{\rm CO} < 10^{-3}$ |
| Gas mass within 50<r<110 au | 0.05-0.1 | not stated | Msun | 5 | gas mass within $50<r<110$ au of $0.05-0.1\ {\rm M_\odot}$ |
| Gas-to-dust ratio at ring peak | 70-400 | not stated | dimensionless | 5 | we estimate the gas-to-dust surface density ratio at the dust surface density peak to be $70-400$ |
| Midplane pressure peak (fiducial) | ~21 (X_CO/1e-4)^-0.5 at r~80 au | not stated | microPa | 4 | The $P_{\rm mid}$ profile peaks at $r\sim80$ au with $\sim21(X_{\rm CO}/10^{-4})^{-0.5}\ {\rm \mu Pa}$ |
| Turbulence alpha_turb | ~2e-4 | not stated | dimensionless | 6 | When $\alpha_{\rm turb}$ is set to $2\times10^{-4}$, the observed width of the dust ring is well reproduced. |
| Fragmentation velocity | ~1 | not stated | m s^-1 | 6 | $v_{\rm frag}$ is estimated to be $\sim 1\ {\rm m\ s^{-1}}$ at the dust ring |
| Planet mass from gap depth | 0.1-2 | not stated | Mjup | 5 | we can estimate the mass of the planet of $0.1-2\ M_{\rm jup}$ for a range of turbulence parameter $\alpha = 10^{-4}-10^{-2}$ |
| C18O peak brightness temperature | ~35 | not stated | K | 7 | reaches $\sim35$ K at the peak |

## Qualitative findings

- Midplane pressure peak coincides with the dust ring, showing dust trapping at a pressure maximum  
  > "This is direct evidence that the dust grains are radially trapped at the pressure maximum." (4.1 Gas surface density profile)
- Gas surface density drops interior to ring, consistent with a gap from a Jupiter-mass planet  
  > "The gas surface density drop at radii interior to the ring is consistent with a gas gap induced by a Jupiter-mass planet." (abstract)

## Claim tuples

- H: Pressure-broadened CO wings are detectable and constrain gas surface density in J1604 | E: Azimuthally stacked CO J=3-2 spectra fitted with Voigt radiative transfer model vs Gaussian | R: Wings follow ~v^-2; Gaussian fits fail; Voigt model fits | F: Pressure-broadened wings detected and give gas surface density independent of CO/H2 up to a X_CO^-0.5 factor | **supported**
- H: Dust ring is a gas pressure maximum | E: Midplane pressure profile compared to dust ring | R: Pressure peaks at r~80 au matching dust peak | F: Direct evidence of dust trapping | **supported**
- H: Disk turbulence level | E: Advection-diffusion dust profiles compared with observed ring width | R: alpha=2e-4 reproduces width | F: Weak turbulence alpha ~2e-4 | **supported**
- H: Disk has enough gas for planet formation | E: Integrate gas surface density over 50-110 au | R: 0.05-0.1 Msun | F: Sufficient mass for planetary system formation | **supported**

## Reasoning

- Why this data: J1604 is lowest-inclination exoALMA disk, avoiding beam smearing of spectral shape  
  > "this disk is the lowest-inclination disk among the exoALMA sample (cite: Curone_exoALMA), which is preferable for the analysis as we can avoid the beam-smearing effect on the spectral shape." (1 Introduction)
- Why this method: _not stated_
- Alternative: High-temperature Gaussian component, turbulence, non-Keplerian motion, and disk winds rejected as origin of wings  
  > "Therefore, the observed broad line wings cannot be explained by a high-temperature component." (3.1 Stacked spectra)
- How they decided it was enough: _not stated_
- Limitation (authors): CO/H2 ratio uncertain; absolute gas surface density scales as X_CO^-0.5  
  > "We note that the CO/H$_2$ ratio remains uncertain in this study." (6 Summary)
- Limitation (authors): Dust opacity model uncertainty affects gas-to-dust ratio; limited spatial resolution  
  > "there might be a large uncertainty in the dust opacity model." (4.4 Caveats)
- Caveat (inferred, ours): Midplane temperature is assumed (14 or 30 K) and not constrained by CO data
- Caveat (inferred, ours): Parametric vertical temperature model with 7 free parameters may be degenerate
- Caveat (inferred, ours): Q>1 argument used to pin X_CO is indirect and circular for deriving the final surface density range
- Caveat (inferred, ours): Low inclination makes stacking depend on weak velocity shifts

## Reproducibility

- Data public (paper): Band 3 and C18O data downloaded from ALMA archive; exoALMA data from large program  
  > "We obtained the visibility data from the ALMA science archive (# 2015.1.00819.S; PI. L. Ricci)." (Appendix: Data reduction of the Band 3 image)
- Products in archive: _not stated_
- Missing: exoALMA CO cube (Loomis et al.) and Band 7 continuum image processing
- Missing: Custom radiative transfer code for Voigt line modeling not released
- Missing: Per-channel noise and fit range for CO fits
- Data volume (inferred): ~100-300 GB for the exoALMA CO cube plus archival Band 3, Band 6 and C18O data (image products are much smaller)
- Score (inferred): 3/5, Analysis is clearly described with priors and MCMC settings, but code is not released, relies on exoALMA cubes and companion papers, and some fit details are missing.
- Rediscovery candidate: no, Key results depend on a custom radiative transfer code and exoALMA cubes processed in companion papers; recipe is incomplete.

## Links

- Method: (cite: yosh22) (Pressure-broadened line wing method)
- Method: (cite: Loomis_exoALMA) (exoALMA CO cube imaging)
- Method: (cite: Longarini_exoALMA) (Hydrostatic density structure)
- Companion: (cite: Teague_exoALMA) (exoALMA overview)
- Companion: (cite: Curone_exoALMA) (Continuum images and geometry)
- Companion: (cite: stad23) (Earlier ALMA Band 6 observations of J1604)
- Related: exoALMA
- Related: MAPS

## Checks

```json
{
 "quotes": 89,
 "quotes_ok": 89,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2018.1.01255.S"
 ],
 "codes_printed_but_missing": [
  "2017.A.01255.S"
 ],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 94,
  "stated": 65,
  "rate": 0.691
 },
 "evidence_ok": true
}
```
