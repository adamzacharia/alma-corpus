# Temperature, Mass, and Turbulence: A Spatially Resolved Multiband Non-LTE Analysis of CS in TW Hya

`2018ApJ...864..133T` | The Astrophysical Journal 2018 | first author: Teague, Richard | arXiv: 1808.01768 | DOI: 10.3847/1538-4357/aad80e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What are the temperature, CS column density, H2 density and non-thermal broadening in the TW Hya disk, derived from three CS transitions, and what minimum disk mass do they imply?  
  > "We present an analysis of CS in TW Hya using the $J=7-6$, $5-4$ and $3-2$ transitions imaged at $\sim 0.5\ensuremath{''}$ spatial resolution" (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance d = 60.1 pc  
  > "TW Hya, the nearest protoplanetary disk at $d = 60.1$ pc (cite: Bailer-Jones_ea_2018) with a near face-on inclination of $i \approx 6\ensuremath{^\circ}$." (Introduction); distance from Bailer-Jones et al. 2018  
  > "TW Hya, the nearest protoplanetary disk at $d = 60.1$ pc (cite: Bailer-Jones_ea_2018) with a near face-on inclination of $i \approx 6\ensuremath{^\circ}$." (Introduction)

## Data provenance

- ALMA projects: 2016.1.00440.S, 2013.1.00387.S
- bands: Band 4, Band 6, Band 7  
  > "342.882850 GHz and 146.969029 GHz in Bands 7 and 4, respectively." (Observations)
- frequencies and spectral setup: Spectral window on each CS line, 15.259 kHz channel spacing  
  > "the correlator was set up to have a spectral window covering the CS transition with a channel spacing of 15.259 kHz." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Band 4: 18.58 m to 1.40 km; Band 7: 15.10 m to 0.70 km  
  > "with baselines spanning 18.58 m to 1.40 km and a total on-source time of 138.73 minutes." (Observations)
- angular resolution: ~0.5-0.6 arcsec beams (0.57x0.50, 0.59x0.47, 0.57x0.51)  
  > "$J = 3 - 2$ & 146.96904 & 14.11 & 35 & 2.0 & 320 & $0.57 \times 0.50$" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Band 4: 138.73 min; Band 7: 47.75 min  
  > "a total on-source time of 47.75 minutes" (Observations)
- observing dates: Band 4: 22, 25, 27 Oct 2016; Band 7: 2 Dec 2016  
  > "Band 4 data were taken in October 2016 over the 22$^{\rm nd}$, 25$^{\rm th}$ and 27$^{\rm th}$" (Observations)
- pi or archival as stated: _not stated_
- Line: CS J=3-2 (146.96904 GHz)
- Line: CS J=5-4 (244.93556 GHz)
- Line: CS J=7-6 (342.88285 GHz)
- External data: Collisional rate coefficients for CS-H2  
  > "We use the collision rates from (cite: Denis-Alpizar_ea_2018)" (Non-LTE Modelling) [from (cite: Denis-Alpizar_ea_2018)]
- External data: Stellar mass fixed at 0.65 Msun  
  > "The stellar mass was fixed at $0.65~M_{\rm sun}$ (cite: Qi_ea_2004)" (Observational Results) [from (cite: Qi_ea_2004)]
- External data: Literature continuum fluxes for flux-scale check  
  > "using flux measurements from (cite: Qi_ea_2004; Qi_ea_2006; Hughes_ea_2009; Tsukagoshi_ea_2016) and (cite: Zhang_ea_2016)." (Flux Calibration) [from Qi 2004, 2006; Hughes 2009; Tsukagoshi 2016; Zhang 2016]
- External data: Surface density profiles compared with minimum-mass result  
  > "we additionally plot surface density profiles from (cite: Gorti_ea_2011), used in (cite: Bergin_ea_2013) to model the HD flux" (Minimum Disk Mass) [from Gorti 2011; Trapman 2017; van Boekel 2017]

## Processing

### Calibration

- pipeline or manual: Provided calibration scripts, then phase self-calibration  
  > "The data were initially calibrated with the provided scripts. Phase self-calibration was performed using `CASA` v4.7." (Observations)
- casa version: CASA v4.7 (self-cal); v5.2 (imaging)  
  > "Imaging was performed in `CASA` v5.2." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Quasars J1107-449 and J1037-2934 as amplitude and phase calibrators  
  > "The quasars J1107-449 and J1037-2934 were used as amplitude and phase calibrators for both bands." (Observations)
- flux scale uncertainty: 10% assumed for all three bands  
  > "In the following we assume a 10% flux calibration uncertainty for all three bands." (Observations)
- self calibration: Phase self-cal, gain tables from collapsed continuum images applied to line spws  
  > "Gain tables were generated on collapsed continuum images then applied to the line spectral windows." (Observations)

### Imaging

- task: CLEAN in CASA 5.2; fixvis to recentre  
  > "Each image was centred on the peak of the continuum using the `fixvis` command" (Observations)
- deconvolver: _not stated_
- weighting robust: Band 6 Briggs robust 0.5; Bands 4 and 7 natural weighting (table lists robust 2.0)  
  > "the band 6 data were imaged using a robust weighting using s Briggs parameter of 0.5." (Observations)
- uv taper: 320 kλ (J=3-2), 230 kλ (J=7-6)  
  > "$J = 7 - 6$ & 342.88285 & 65.83 & 14 & 2.0 & 230" (Table 1)
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian mask  
  > "All cubes `CLEAN`ed using a Keplerian mask using parameters consistent with previous observations of TW Hya." (Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.57x0.50, 0.59x0.47, 0.57x0.51 arcsec  
  > "$J = 5 - 4$ & 244.93556 & 35.27 & 19 & 0.5 & - & $0.59 \times 0.47$" (Table 1)
- final rms: 0.56, 0.46, 0.39 K per channel (3-2, 5-4, 7-6)  
  > "$J = 7 - 6$ & 342.88285 & 65.83 & 14 & 2.0 & 230 & $0.57 \times 0.51$ & $74.9$ & 0.39 & 10.3" (Table 1)

### Inherited from earlier work

- Keplerian mask parameters  
  > "using parameters consistent with previous observations of TW Hya." (Observations) [from previous TW Hya observations (no citation given)]
- Band 6 CS 5-4 data (project 2013.1.00387.S)  
  > "Band 6 data comes from project 2013.1.00387.S, originally published in (cite: Teague_ea_2016)." (Observations) [from (cite: Teague_ea_2016)]
- Deprojection and spectral shifting of data by Keplerian rotation  
  > "Following (cite: Teague_ea_2016) (cite: Yen_ea_2016; Matra_ea_2017), we deproject the data spatially and spectrally accounting for the rotation of the disk." (Observational Results) [from Teague 2016; Yen 2016; Matra 2017]
- Convolving rotation pattern before likelihood in Keplerian fit  
  > "Following (cite: Walsh_ea_2017) we convolve the rotation pattern before calculation of the likelihood." (Observational Results) [from (cite: Walsh_ea_2017)]
- LTE rotation diagram formalism  
  > "Following (cite: Goldsmith_Langer_1999), in the optically thin limit the integrated flux can be related to the level population of the upper energy state," (LTE Analysis) [from (cite: Goldsmith_Langer_1999)]

### Not stated but needed to reproduce (our reading)

- Keplerian mask parameters and clean thresholds/iterations
- Robust value for Bands 4/7 (table says 2.0, text says natural) and exact Gaussian taper definitions
- Line-free channels and continuum subtraction method
- Self-calibration solution intervals and number of iterations
- Image cell and size
- Initial walker positions and prior on line centres/noise parameters
- Number of spws/execution blocks combined and pipeline version
- Hanning smoothing implementation details

## Analysis recipe

1. **Calibrate and image CS cubes**: Provided scripts, phase self-cal, CLEAN with Keplerian mask, different weighting/taper per band to match beams  
  > "To mitigate any differences between observations due to the different beam sizes, we applied a different weighting scheme to each transition." (Observations)
   - software: CASA
   - parameter: Beams ~0.57x0.5 arcsec; robust 0.5 for B6  
  > "the band 6 data were imaged using a robust weighting using s Briggs parameter of 0.5." (Observations)
   - fitting: _not stated_
   - validation: Continuum fluxes compared with literature  
  > "No significant deviation is found relative to the literature values suggesting the flux calibration was performed adequately." (Flux Calibration)
2. **Fit disk geometry**: Fit Keplerian pattern to first moment maps  
  > "we fit a Keplerian rotation pattern, $v_{\rm Kep} = \sqrt{GM_{\star} \, / \, r}$ to the first moment maps." (Observational Results)
   - parameter: Free: centre, i, PA, vLSR  
  > "The disk centre, $(x_0,\, y_0)$, inclination $i$, position angle, PA and systemic velocity, $v_{\rm LSR}$, were allowed to vary." (Observational Results)
   - assumption: M* fixed at 0.65 Msun  
  > "The stellar mass was fixed at $0.65~M_{\rm sun}$ (cite: Qi_ea_2004)" (Observational Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Deproject and azimuthally average spectra**: Shift each pixel by projected Keplerian velocity to common velocity, bin into 4 au annuli, average; fit Gaussian per annulus  
  > "The data were then binned into annuli with a width of 4 au and then averaged to increase the signal-to-noise ratio." (Observational Results)
   - parameter: 4 au annuli  
  > "The data were then binned into annuli with a width of 4 au" (Observational Results)
   - fitting: Gaussian line profile with width and peak T_B  
  > "A Gaussian line profile, characterised by a line width $\Delta V$ and the peak brightness temperature $T_B$, was fit to each azimuthally averaged spectrum ." (Observational Results)
   - validation: _not stated_
4. **LTE fit of Tex and N(CS)**: Rotation-diagram style fit of integrated fluxes with optical depth correction, pixel-by-pixel and on annuli  
  > "allows us fit for $\left\{T_{\rm ex},\ N({\rm CS})\right\}$, self-consistently accounting for possible optical depth effects." (LTE Analysis)
   - software: emcee
   - parameter: 256 walkers, 200 burn-in, 100 sampling steps; 10% flux systematic  
  > "We used 256 walkers which took 200 steps to burn-in before taking an additional 100 to sample the posterior distribution." (LTE Analysis)
   - assumption: LTE; thermal broadening only for tau  
  > "which can be calculated assuming only thermal broadening, a reasonable assumption given the low levels of turbulence previously reported." (LTE Analysis)
   - fitting: emcee; uniform priors Tex 10-150 K, log N 9-14, tau<1  
  > "To take this into account we include a prior that $\tau < 1$ for all lines." (LTE Analysis)
   - validation: _not stated_
5. **Non-LTE slab fit of spectra**: Isothermal slab with RADEX grid (pyradex, 40 samples per axis, interpolated), sampled at fine resolution then Hanning smoothed; Gaussian-process noise  
  > "a large grid in $\{T_{\rm kin},\, n({\rm H}_2),\, N({\rm CS}),\, \Delta V\}$ space was run using `pyradex`[^1], and linearly interpolated between points." (Non-LTE Modelling)
   - software: RADEX, pyradex, emcee, celerite
   - parameter: 13 free params per radius; 256 walkers, 1500 burn-in, 250 sampling steps  
  > "Each fit consisted of 256 walkers, each taking 1500 steps for a burn-in period, then an additional 250 to sample the posterior distribution." (Non-LTE Modelling)
   - assumption: Thermal H2 ortho-para ratio; slab geometry; no beam-smear correction  
  > "We do not attempt to correct for such beam smear effects." (Non-LTE Modelling)
   - fitting: emcee; uniform priors T 10-150 K, log n 4-10, log N 9-14, log M -5 to 0 (also linear M 0-1)  
  > "We additionally run a set of models where we fit for $\mathcal{M}$ rather than $\log_{10}\mathcal{M}$ for which we impose a prior of $\mathcal{M} = \mathcal{U}(0,\ 1)$." (Non-LTE Modelling)
   - validation: Compared with LTE results; grid interpolation checked; Matern-3/2 vs SHO kernels  
  > "A simple harmonic oscillator kernel was also tested however no significant difference was found between kernels." (Non-LTE Modelling)
6. **Derive minimum gas surface density and disk mass**: Convert minimum midplane n(H2) to Sigma_gas with Gaussian vertical structure and pressure scale height, integrate  
  > "For this estimate we use both fits from Section [4](#sec:NonLTE_Modelling) for the minimum $n({\rm H_2})$ to infer a minimum $\Sigma_{\rm gas}$" (Minimum Disk Mass)
   - assumption: CS emission from <~1 H_mid; M*=0.65 Msun; mu in H_mid  
  > "Observations of the edge-on Flying Saucer have shown CS emission to arise from $\lesssim 1 H_{\rm mid}$ (cite: Dutrey_ea_2017)." (Minimum Disk Mass)
   - fitting: _not stated_
   - validation: Compared with HD-based masses and literature surface density profiles  
  > "fully consistent with the estimates from HD emission" (Minimum Disk Mass)

## Software

- **CASA** 4.7 (self-cal), 5.2 (imaging): Self-calibration, imaging, fixvis  
  > "Phase self-calibration was performed using `CASA` v4.7." (Observations)
- **emcee** : MCMC posteriors for LTE and non-LTE fits  
  > "We use `emcee` (cite: emcee) to calculate posterior distributions of $T_{\rm ex}$ and $\log_{10}N({\rm CS})$." (LTE Analysis)
- **RADEX** : Excitation calculations  
  > "the excitation calculations are performed with the 0-D code `RADEX` (cite: vanderTak_ea_2007)" (Non-LTE Modelling)
- **pyradex** : Grid of RADEX models for interpolation  
  > "a large grid in $\{T_{\rm kin},\, n({\rm H}_2),\, N({\rm CS}),\, \Delta V\}$ space was run using `pyradex`[^1]" (Non-LTE Modelling)
- **celerite** : Gaussian process noise model  
  > "modelling the noise component using Gaussian Processes, implemented with the Python package `celerite` (cite: celerite)." (Non-LTE Modelling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk inclination | 6.8 | ±0.1 | deg | 2 | yielding an inclination $i = 6.8 \pm 0.1\ensuremath{^\circ}$, ${\rm PA} = 151 \pm 1\ensuremath{^\circ}$ |
| Position angle | 151 | ±1 | deg | 2 | ${\rm PA} = 151 \pm 1\ensuremath{^\circ}$ |
| Systemic velocity | 2842 | ±2 | m/s | 2 | $v_{\rm LSR} = 2842 \pm 2~{\rm ms^{-1}}$ |
| Minimum disk mass | 3e-4 | not stated | Msun | 6 | we find an average minimum disk mass of $3\times10^{-4}~M_{\rm sun}$ |
| Turbulence Mach number upper limit | ≲0.1 | 2sigma upper limit | dimensionless | 5 | finding $\mathcal{M} \lesssim 0.1$ across the disk |
| Tkin at 100 au | 28 | not stated | K | 5 | $T_{\rm kin} = 28$ K at 100 au compared to 12 K as in (cite: Teague_ea_2016) |
| Tex inner 30 au (LTE) | ≈40, dropping to 20 K at 200 au | not stated | K | 4 | Within the inner 30 au a constant temperature of $T_{\rm ex} \approx 40$ K is found, slowly dropping to 20 K at 200 au. |
| CS desorption temperature | ≈31 | not stated | K | 0 | The binding energy of CS is 1900 K resulting in a desorption temperature of $T_{\rm desorb} \approx 31$ K |

## Qualitative findings

- CS column density shows knees at 90 au and 160 au; azimuthally symmetric structure  
  > "The column density of CS was found to have two significant knees at 90 and 160 au" (Summary)
- Transitions are thermalized out to about 190 au, giving only lower limits on n(H2) inside that radius  
  > "high H$_2$ densities are found resulting in thermalisation of the transitions out to $\approx 190$ au." (Non-LTE Modelling)

## Claim tuples

- H: Multi-transition CS data can give spatially resolved gas temperature and column density out to large radii | E: LTE and non-LTE fits of azimuthally averaged spectra | R: T~40 K inner to <~20 K at 200 au; both methods agree | F: Temperature and N(CS) profiles obtained to 230 au | **supported**
- H: Non-thermal broadening is small in TW Hya | E: Non-LTE fit with temperature constrained by three lines | R: 2sigma upper limit M<~0.1 out to 230 au | F: Turbulence is weak | **supported**
- H: CS excitation constrains the H2 density and the disk mass | E: Convert n(H2) limits to Sigma_gas and integrate | R: Minimum disk mass 3e-4 Msun | F: Consistent with HD estimates; van Boekel profile most consistent in outer disk | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Multiple transitions break degeneracy between temperature and column density  
  > "the degeneracy between column density and temperature could not be broken without assuming an underlying physical structure." (Introduction)
- Alternative: Simple harmonic oscillator noise kernel tested, no significant difference  
  > "A simple harmonic oscillator kernel was also tested however no significant difference was found between kernels." (Non-LTE Modelling)
- How they decided it was enough: _not stated_
- Limitation (authors): Beam smear not corrected, affecting inner 90-100 au  
  > "We do not attempt to correct for such beam smear effects." (Non-LTE Modelling)
- Limitation (authors): Neighbouring annuli are correlated within a beam  
  > "Although in the following text we treat each annulus as independent, in practice they will still be correlated over the size of the beam." (Observational Results)
- Caveat (inferred, ours): Single-layer, isothermal slab assumption for all three lines
- Caveat (inferred, ours): Minimum mass depends on assumed scale height and emitting height
- Caveat (inferred, ours): Image-plane fitting ignores spatially correlated noise

## Reproducibility

- Data public (paper): Data cited by ALMA project codes in acknowledgments  
  > "ADS/JAO.ALMA#2016.1.00440.S and" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Mask and clean parameters
- Missing: Self-calibration details
- Missing: Analysis code not released
- Data volume (inferred): ~100-300 GB raw across three bands
- Score (inferred): 3/5, Public data and detailed fitting recipe, but imaging, self-cal and mask details are missing and no code is released.
- Rediscovery candidate: yes, Public data, numeric results and a mostly complete recipe.

## Links

- Method: (cite: Teague_ea_2016) (Deprojection method and the band 6 data)
- Method: (cite: Flaherty_ea_2018) (Image-plane versus uv-plane fitting)
- Companion: (cite: Teague_ea_2016) (Earlier CS 5-4 and CN analysis of TW Hya)
- Companion: (cite: Teague_ea_2017) (Surface density perturbation at 90 au)

## Checks

```json
{
 "quotes": 79,
 "quotes_ok": 79,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 62,
  "rate": 0.697
 },
 "evidence_ok": true
}
```
