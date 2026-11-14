# Large-scale Asymmetries in the Transitional Disks of SAO 206462 and SR 21

`2014ApJ...783L..13P` | The Astrophysical Journal Letters 2014 | first author: Pérez, Laura M. | arXiv: 1402.0832 | DOI: 10.1088/2041-8205/783/1/L13

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What is the large-scale structure of the dust emission in the transitional disks of SAO 206462 and SR 21, and are the asymmetries consistent with vortex-like features?  
  > "Nevertheless, a ring alone is not a good fit, and the addition of a vortex prescription describes these data much better." (abstract)
- Target **SAO 206462**: coordinates 15:15:48.448 -37:09:16.06 (J2000)  
  > "SAO 206462 is an isolated Herbig Ae/Be star (F4Ve, $1.7\:M_{\odot}$), at a distance of 142 pc in the Sco-OB2 association" (Introduction); "| SAO 206462 | 15:15:48.448 | $-$37:09:16.06 |" (Table 1); z/distance 142 pc  
  > "SAO 206462 is an isolated Herbig Ae/Be star (F4Ve, $1.7\:M_{\odot}$), at a distance of 142 pc in the Sco-OB2 association" (Introduction); "| SAO 206462 | 15:15:48.448 | $-$37:09:16.06 |" (Table 1); distance from Müller et al. 2011 (cite: 2011A&A...530A..85M)  
  > "SAO 206462 is an isolated Herbig Ae/Be star (F4Ve, $1.7\:M_{\odot}$), at a distance of 142 pc in the Sco-OB2 association" (Introduction); "| SAO 206462 | 15:15:48.448 | $-$37:09:16.06 |" (Table 1)
- Target **SR 21**: coordinates 16:27:10.281 -24:19:12.88 (J2000)  
  > "SR 21 is a young G3 star ($2.5\:M_{\odot}$) in the $\rho$-Ophiuchus star forming region at a distance of 119 pc" (Introduction); "| SR 21      | 16:27:10.281 | $-$24:19:12.88 |" (Table 1); z/distance 119 pc  
  > "SR 21 is a young G3 star ($2.5\:M_{\odot}$) in the $\rho$-Ophiuchus star forming region at a distance of 119 pc" (Introduction); "| SR 21      | 16:27:10.281 | $-$24:19:12.88 |" (Table 1); distance from Lombardi et al. 2008 (cite: 2008A&A...480..785L)  
  > "SR 21 is a young G3 star ($2.5\:M_{\odot}$) in the $\rho$-Ophiuchus star forming region at a distance of 119 pc" (Introduction); "| SR 21      | 16:27:10.281 | $-$24:19:12.88 |" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00724.S
- bands: 0.45 mm (690 GHz)  
  > "Observations at 0.45 mm (690 GHz) of SAO 206462 and SR 21 were obtained during ALMA Cycle 0 between June-July 2012" (Observations and Calibration)
- frequencies and spectral setup: Four spectral windows, 1.875 GHz each, 3840 channels of 0.488 MHz (~0.2 km/s), 7.5 GHz total  
  > "3840 channels of 0.488 MHz width ($\sim0.2\:\textrm{km~s}^{-1}$), for a total bandwidth of 7.5 GHz in dual polarization" (Observations and Calibration)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 50 to 500 m  
  > "with baselines ranging from 50 to $500\:$m" (Observations and Calibration)
- angular resolution: Continuum beams 0.27x0.19 arcsec (SAO 206462), 0.29x0.18 arcsec (SR 21)  
  > "$0.27'' \times 0.19''$" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: Continuum RMS 0.0020 (SAO 206462) and 0.0011 (SR 21) Jy/beam; line RMS 0.11 and 0.07 Jy/beam per 0.5 km/s channel  
  > "RMS noise level in a 0.5 km s$^{-1}$ channel." (Table 1)
- time on source: 25 min for both targets  
  > "A total 25 min on-source time was obtained for both targets." (Observations and Calibration)
- observing dates: June-July 2012 (Cycle 0)  
  > "were obtained during ALMA Cycle 0 between June-July 2012" (Observations and Calibration)
- pi or archival as stated: _not stated_
- Line: 12CO J=6-5 (not stated)
- Other facility **Near-IR H-band polarized intensity (literature)**: Scattered light images compared with ALMA residuals  
  > "we present polarized intensity maps at H-band of both disks" (Discussion)
- External data: H-band polarized intensity images of SAO 206462 and SR 21  
  > "we present polarized intensity maps at H-band of both disks (cite: 2012Muto; 2013ApJ...767...10F)" (Discussion) [from Muto et al. 2012 (cite: 2012Muto); Follette et al. 2013 (cite: 2013ApJ...767...10F)]
- External data: Dust surface density at cavity edge ~0.1 g cm^-2 from 850 um observations  
  > "constrained the surface density at the edge of the cavity to be $\Sigma_{dust}\sim0.1\:\textrm{gm~cm}^{-2}$ for both SAO 206462 and SR 21" (Observational Results) [from Andrews et al. 2011 (cite: 2011ApJ...732...42A)]
- External data: Dust opacity 10 cm^2/g at 450 um  
  > "a dust opacity of $\kappa_{\nu}=10\:\textrm{cm}^{2}\:\textrm{g}^{-1}$ at $450\:\mu$m (cite: 1990AJ.....99..924B)" (Discussion) [from Beckwith et al. 1990 (cite: 1990AJ.....99..924B)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (flux), 3C 279 (bandpass)  
  > "the absolute flux scale was measured using Titan observations" (Observations and Calibration)
- flux scale uncertainty: _not stated_
- self calibration: Amplitude and phase self-calibration after standard phase referencing  
  > "amplitude and phase self-calibration was performed after standard phase referencing" (Observations and Calibration)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "obtained using Briggs weighting with a robust of 0.5" (Observations and Calibration)
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
- final beam: Continuum 0.27x0.19 arcsec PA 53 deg (SAO 206462); 0.29x0.18 arcsec PA -81 deg (SR 21)  
  > "$0.29'' \times 0.18''$" (Table 1)
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CASA version
- Self-calibration solution intervals and reference antenna
- Cell size, image size, deconvolver and masking
- MCMC walkers, steps, burn-in, priors and parameter bounds
- Flux calibrator model for Titan and flux uncertainty
- How the moment maps were made (channel range, clip)
- Continuum channel selection / line-free channels

## Analysis recipe

1. **Image continuum and CO moment maps**: Visibilities calibrated and imaged in CASA with Briggs weighting; CO moment 0 and 1 maps made  
  > "Visibilities were calibrated and imaged in CASA." (Observations and Calibration)
   - software: CASA
   - parameter: robust = 0.5  
  > "obtained using Briggs weighting with a robust of 0.5" (Observations and Calibration)
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate optical depth and brightness temperature**: Brightness temperature computed without Rayleigh-Jeans approximation; optical depth from literature surface density and opacity  
  > "We also computed the brightness temperature ($T_b$) of the emission without the Raleigh-Jeans approximation." (Observational Results)
   - assumption: kappa = 10 cm^2/g at 450 um  
  > "Assuming a dust opacity of $\kappa_{\nu}=10\:\textrm{cm}^{2}\:\textrm{g}^{-1}$ at $450\:\mu$m" (Observational Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit ring and ring+vortex models to visibilities**: Gaussian radial ring and Lyra & Lin vortex (Gaussian in r and theta) Fourier transformed and sampled at observed uv-positions; chi^2 minimized; PA fixed from CO moment 1; center and inclination free  
  > "Each model realization is Fourier transformed and sampled at the same *uv*-positions as the observation." (Analysis)
   - software: emcee
   - parameter: SR 21 ring+vortex inclination fixed to 15 deg  
  > "Thus, we fixed the inclination to $i=15^{\circ}$ for SR 21 ring+vortex modeling" (Analysis)
   - assumption: Ring emission axisymmetric; PA fixed to 62 deg (SAO 206462) and 16 deg (SR 21)  
  > "In our modeling the ring emission is assumed to be axisymmetric." (Analysis)
   - fitting: Affine-invariant MCMC (emcee), minimizing chi^2  
  > "The best-fit model was found by minimizing the $\chi^2$ statistic using the latest implementation of the affine-invariant MCMC *emcee* software" (Analysis)
   - validation: Compared reduced chi^2 and residual maps of ring vs ring+vortex  
  > "The addition of a vortex prescription in the fitting improves the resulting residual map and $\chi^2$ of the fit" (Analysis)
4. **Derive vortex mass and turbulence**: Convert vortex flux to mass; use vortex aspect ratio and Stokes number to infer turbulent velocity  
  > "The vortex aspect ratio derived for SAO 206462 and SR 21 would then require turbulent velocities of about $90\:\textrm{m~s}^{-1}$ and $68\:\textrm{m~s}^{-1}$ respectively" (Discussion)
   - assumption: T=35 K, gas-to-dust 100, kappa=10 cm^2/g at 450 um for mass  
  > "assuming a temperature of $T=35K$, a gas-to-dust ratio of 100, and a dust opacity of $\kappa_{\nu}=10\:\textrm{cm}^{2}\:\textrm{g}^{-1}$ at $450\:\mu$m" (Discussion)
   - assumption: a=1 mm, rho_s=1 g/cm3, Sigma=10 g/cm2, St~1e-2; gas T=50 K for sound speed  
  > "Dust grains with size $a=1$ mm and internal density $\rho_s=1$ g cm$^{-3}$, embedded in a disk with a surface density of $\Sigma=10$ g cm$^{-2}$" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration and imaging  
  > "Visibilities were calibrated and imaged in CASA." (Observations and Calibration)
- **emcee** : MCMC fitting of ring and vortex models  
  > "using the latest implementation of the affine-invariant MCMC *emcee* software" (Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Asymmetry contrast SAO 206462 | 1.5 | 0.02 | dimensionless | 1 | $1.5\pm0.02$ in SAO 206462 and $1.9\pm0.01$ in SR 21 |
| Asymmetry contrast SR 21 | 1.9 | 0.01 | dimensionless | 1 | $1.5\pm0.02$ in SAO 206462 and $1.9\pm0.01$ in SR 21 |
| Reduced chi^2 ring vs ring+vortex, SAO 206462 | 1.18 vs 1.05 | not stated | dimensionless | 3 | $\chi^2_{red}=1.18$  / $\chi^2_{red}=1.05$ |
| Reduced chi^2 ring vs ring+vortex, SR 21 | 1.39 vs 1.06 | not stated | dimensionless | 3 | $\chi^2_{red}=1.39$  / $\chi^2_{red}=1.06$ |
| Vortex fraction of total flux | 15% (SAO 206462), 28% (SR 21) | not stated | percent | 3 | The vortex encompasses 15% of the total flux density for SAO 206462 and 28% for SR 21. |
| Vortex mass | ~2 | not stated | M_Jup | 4 | The flux density in the asymmetry corresponds to a mass (dust+gas) of $\sim2\:M_{\textrm{Jup}}$ for both SAO 206462 and SR 21 |
| Vortex aspect ratio SAO 206462 / SR 21 | 7.1 / 2.8 | not stated | dimensionless | 3 | $\sigma_{\phi,V}/\sigma_{r,V}=7.1$ for SAO 206462 and $\sigma_{\phi,V}/\sigma_{r,V}=2.8$ for SR 21 |
| Required turbulent velocity | 90 (SAO 206462), 68 (SR 21) | not stated | m/s | 4 | turbulent velocities of about $90\:\textrm{m~s}^{-1}$ and $68\:\textrm{m~s}^{-1}$ respectively |
| Ring radius (ring+vortex) | 65.3 AU (SAO 206462), 35.0 AU (SR 21) | 0.1 AU | AU | 3 | $65.3\pm0.1$ |
| Peak brightness temperature | ~30 K (SAO 206462), ~35 K (SR 21) | not stated | K | 2 | $T_b\sim30$ K for SAO 206462, and $T_b\sim35$ K for SR 21 |

## Qualitative findings

- 12CO emission is compact and mostly symmetric, unlike the dust.  
  > "the gaseous component from the $^{12}$CO moment 0 map appears to be quite compact and mostly symmetric" (Observational Results)
- Significant residuals remain after ring+vortex fit, suggestive of spiral-like structure.  
  > "Significant residuals remain that are suggestive of spiral-like structure" (Conclusions)

## Claim tuples

- H: Do the dust continuum rings of SAO 206462 and SR 21 require an azimuthal asymmetry? | E: Fit ring and ring+vortex models to visibilities | R: Reduced chi^2 drops from 1.18 to 1.05 and 1.39 to 1.06 | F: A ring alone is a poor fit; a vortex-like asymmetry fits better | **supported**
- H: Could the asymmetries be steady-state vortices? | E: Use vortex aspect ratio with assumed Stokes number to infer turbulence | R: Turbulent velocity ~16-22% of sound speed | F: If vortices, turbulence must be large | **partially**
- H: Does the submm emission trace the near-IR structures? | E: Compare residuals with H-band images | R: SR 21 differs; some overlap for SAO 206462 spirals | F: SR 21 scattered light differs from submm; SAO 206462 residuals suggest spiral-like structure | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Spiral-arm fit to residuals not attempted due to many parameters and low signal.  
  > "Given the low signal of these features and degeneracies between such large number of parameters, we decided not to proceed with such a fit." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Emission may be partly optically thick so asymmetries may not trace mass; masses are lower limits.  
  > "These are lower limits on the vortex mass, given the uncertainty in optical depth at this wavelength." (Discussion)
- Caveat (inferred, ours): Morphological Gaussian models are not unique; temperature variations could mimic asymmetries
- Caveat (inferred, ours): Fixing the SR 21 inclination biases the fit
- Caveat (inferred, ours): Turbulence estimate depends on assumed Stokes number and surface density
- Caveat (inferred, ours): Uncertainties from MCMC likely underestimate systematics; chi^2 near 1 with correlated noise unclear

## Reproducibility

- Data public (paper): ALMA project 2011.0.00724.S acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA 2011.0.00724.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and self-calibration parameters
- Missing: MCMC configuration and priors
- Missing: Imaging geometry parameters
- Data volume (inferred): ~20-50 GB for two Cycle 0 Band 9 datasets
- Score (inferred): 3/5, Public Cycle 0 data and a simple model with a table of results, but calibration, self-cal and MCMC details are missing.
- Rediscovery candidate: yes, Data are public, the model is simple and results are numeric, though some details must be guessed.

## Links

- Method: Lyra & Lin 2013 (cite: 2013Lyra) (Steady-state vortex prescription used for the asymmetry model)
- Method: Foreman-Mackey et al. 2013 (cite: 2013PASP..125..306F) (emcee sampler)
- Companion: Isella et al. 2013 (cite: 2013ApJ...775...30I) (LkHa 330 asymmetry, comparison)

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 41,
  "rate": 0.554
 },
 "evidence_ok": true
}
```
