# WISDOM Project - II. Molecular gas measurement of the supermassive black hole mass in NGC 4697

`2017MNRAS.468.4675D` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Davis, Timothy A. | arXiv: 1703.05248 | DOI: 10.1093/mnras/stw3217

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What is the SMBH mass in NGC4697 from molecular gas kinematics, and does it agree with stellar-kinematic measurements?  
  > "so our new observations allow us to conduct a vital cross check between these two methods." (INTRODUCTION)
- Target **NGC4697**: coordinates ALMA phase centre RA=12:38:35.91, DEC=-05:48:03.1  
  > "we assume a distance of 11.4$\pm$1.1 Mpc for NGC4697 (cite: 2011MNRAS.413..813C), as derived from surface brightness fluctuation measurements in (cite: Tonry:2001ei)." (INTRODUCTION); z/distance 11.4±1.1 Mpc  
  > "we assume a distance of 11.4$\pm$1.1 Mpc for NGC4697 (cite: 2011MNRAS.413..813C), as derived from surface brightness fluctuation measurements in (cite: Tonry:2001ei)." (INTRODUCTION); distance from SBF, Tonry et al. 2001 (via Cappellari et al. 2011)  
  > "we assume a distance of 11.4$\pm$1.1 Mpc for NGC4697 (cite: 2011MNRAS.413..813C), as derived from surface brightness fluctuation measurements in (cite: Tonry:2001ei)." (INTRODUCTION)

## Data provenance

- ALMA projects: 2015.1.00598.S
- bands: _not stated_
- frequencies and spectral setup: 1850 MHz window on CO(2-1), ~2000 km/s coverage, ~1 km/s raw resolution; three 2 GHz continuum windows  
  > "An 1850 MHz correlator window was placed over the CO(2–1) line, yielding a continuous velocity coverage of $\approx$2000 km s$^{-1}$" (ALMA DATA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C36-3  
  > "The C36-3 antenna configuration was used" (ALMA DATA)
- baselines: _not stated_
- angular resolution: 0.54x0.52 arcsec, PA -22 deg (~30x29 pc)  
  > "yielding a synthesised beam of 0$.\!\!^{\prime\prime}$54$\times$0$.\!\!^{\prime\prime}$52 at a position angle of -22$^{\circ}$" (ALMA DATA)
- max recoverable scale: 17 arcsec  
  > "yielding sensitivity to emission on scales up to 17$^{\prime \prime}$" (ALMA DATA)
- sensitivity: 1.1 mJy/beam per 10 km/s channel; 2.1 mJy/beam per 3 km/s channel; continuum rms 35 uJy  
  > "RMS noise level of 1.1 mJy beam$^{-1}$ in each 10 km s$^{-1}$ channel (or 2.1 mJy beam$^{-1}$ in each 3 km s$^{-1}$ channel)" (ALMA DATA)
- time on source: 574 s, single track  
  > "The total integration time on source was 574 seconds, observed as a single track." (ALMA DATA)
- observing dates: 1 May 2016  
  > "observed with ALMA on the 1st of May 2016" (ALMA DATA)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Other facility **HST ACS F850LP**: Image used to build MGE stellar light model and dust disc inclination  
  > "This was constructed from an *HST* Advanced Camera for Surveys (ACS) F850LP image" (Luminous mass models)
- Other facility **Herschel/Spitzer (HEART) and NED**: Far-IR and radio SED data points  
  > "*Herschel* and *Spitzer Space Telescope* data are taken from the Herschel Almanac of Early Types (HEART) project of Smith et al., in prep." (Continuum emission)
- External data: MGE and M/L used for the figure-of-merit calculation  
  > "calculated by multiplying the MGE of (cite: 2013MNRAS.432.1894S) with the mass-to-light ratio of (cite: 2013MNRAS.432.1709C)" (METHOD & RESULTS) [from (cite: 2013MNRAS.432.1894S); (cite: 2013MNRAS.432.1709C)]
- External data: Previous stellar-kinematic SMBH masses for comparison  
  > "(cite: 2003ApJ...583...92G) found $M_{\rm BH}$ = (1.6$\pm$0.2) $\times$10$^8$ M$_{\odot}$" (Comparison of SMBH mass with other measurements) [from (cite: 2003ApJ...583...92G); (cite: 2011ApJ...729...21S)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA pipeline by regional centre staff  
  > "The raw ALMA data were calibrated using the standard ALMA pipeline, as provided by the ALMA regional centre staff." (ALMA DATA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1256-0547 (amplitude and bandpass); phase J1246-0730  
  > "Amplitude and bandpass calibration were performed using J1256-0547." (ALMA DATA)
- flux scale uncertainty: ~10%  
  > "accounts for the $\approx$10% flux calibration uncertainty in the ALMA data" (Line emission)
- self calibration: _not stated_

### Imaging

- task: CASA; uvcontsub for continuum subtraction  
  > "subtracted from the data in the $uv$ plane using the `CASA` task `uvcontsub`" (ALMA DATA)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "produced using Briggs weighting with a robust parameter of 0.5" (ALMA DATA)
- uv taper: _not stated_
- cell size: 0.1 arcsec  
  > "pixels of 0$.\!\!^{\prime\prime}$1$\times$0$.\!\!^{\prime\prime}$1 were chosen" (ALMA DATA)
- image size: _not stated_
- masking: Interactive cleaning regions; clean to threshold equal to dirty-channel RMS  
  > "cleaned in regions of source emission (identified interactively) to a threshold equal to the RMS noise of the dirty channels" (ALMA DATA)
- multiscale scales: _not stated_
- continuum subtraction: Continuum measured over full line-free bandwidth, subtracted in uv plane  
  > "measured over the full line-free bandwidth, and then subtracted from the data in the $uv$ plane" (ALMA DATA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Clean components re-convolved with Gaussian equal to dirty beam  
  > "re-convolved using a Gaussian beam of full-width-at-half-maximum (FWHM) equal to that of the dirty beam" (ALMA DATA)
- final rms: _not stated_

### Inherited from earlier work

- Fitting procedures and tools described in WISDOM Paper I  
  > "The first paper in this series discussed in detail the tools and fitting procedures developed so far" (INTRODUCTION) [from Onishi et al., 2017]
- Galactic XCO as in Young et al. 2011  
  > "a Galactic X$_{\rm CO}$ conversion factor (as in (cite: 2011MNRAS.414..940Y))" (Line emission) [from (cite: 2011MNRAS.414..940Y)]
- Empirical dust absorption coefficient and beta  
  > "$\kappa_{500\mu m}$ = 0.051 m$^2$ kg$^{-1}$ and $\beta$ = 1.8 (cite: 2016MNRAS.459.1646C)" (Continuum emission) [from (cite: 2016MNRAS.459.1646C)]

### Not stated but needed to reproduce (our reading)

- Number of clean iterations and exact mask definition
- Channel range used for the line-free continuum
- Hanning smoothing details and exact moment-map parameters
- KINMS_MCMC code is unpublished (Davis et al., in prep.); Gibbs sampler settings and convergence criteria not given
- Number of walkers/chains and the fitted cube spatial region
- Exact MGE fitting settings and dust masking regions in the HST image
- Photometric aperture for the continuum flux
- SED data point values and uncertainties

## Analysis recipe

1. **Image CO(2-1) cube and continuum**: Combine and image calibrated visibilities in CASA, uv continuum subtraction, clean, restore with dirty beam  
  > "used the `Common Astronomy Software Applications` (`CASA)` package to combine and image the resultant visibility file" (ALMA DATA)
   - software: CASA
   - parameter: 10 km/s channels (also 3 km/s), robust 0.5, 0.1 arcsec pixels  
  > "we primarily use data with a channel width of 10 km s$^{-1}$" (ALMA DATA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Moment maps, PVD, flux and H2 mass**: Masked moment technique with spatial Gaussian and velocity Hanning smoothing, 1.5 sigma threshold; H2 mass from CO flux  
  > "A three-dimensional mask was then defined by selecting all pixels above a fixed flux threshold of 1.5$\sigma$" (Line emission)
   - assumption: CO(2-1)/CO(1-0) = 0.8 and Galactic XCO  
  > "assuming a typical CO(2-1)/CO(1-0) ratio of 0.8 (cite: 2008AJ....136.2846B)" (Line emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit dust SED**: Modified black body plus fixed-index synchrotron power law fitted with chi2 minimisation to HEART and NED data  
  > "A simple SED model was fitted to these datapoints using the $\chi^2$ minimisation routines `MPFIT`" (Continuum emission)
   - software: MPFIT
   - assumption: beta = 1.8, kappa500 = 0.051 m2/kg, radio spectral index fixed at -0.8  
  > "We fix the radio spectral index to $-0.8$" (Continuum emission)
   - fitting: chi2 minimisation (MPFIT); ALMA point not in the fit  
  > "Our ALMA 1 mm continuum measurement, although not included in the fit, lies on the predicted SED." (Continuum emission)
   - validation: ALMA point lies on predicted SED; agrees with Smith et al. in prep.  
  > "Our ALMA 1 mm continuum measurement, although not included in the fit, lies on the predicted SED." (Continuum emission)
4. **Build luminous mass model**: MGE fit to HST ACS F850LP image; central unresolved Gaussian removed; deprojected to give circular velocity with free M/L  
  > "We subtract this point source by removing the innermost (spatially unresolved) Gaussian from our MGE model" (Gas kinematics)
   - software: MGE_FIT_SECTORS
   - assumption: Negligible dark matter and gas mass at these radii; constant M/L  
  > "We note that dark matter, while important at larger galactocentric distances, is usually negligible at these radii." (Gas kinematics)
   - fitting: _not stated_
   - validation: Test with circular velocity scaled by ±10%  
  > "we re-ran our fitting procedure assuming our MGE model over/underestimated the circular velocity at each radius by $\pm$10%." (Main uncertainties – Luminous mass models, AGN & dust)
5. **Forward-model cube and sample posterior**: KinMS models fitted to whole cube with MCMC (Gibbs sampling, adaptive stepping), full analytic covariance matrix likelihood, LDL^T factorisation  
  > "we utilize an MCMC method with Gibbs sampling and adaptive stepping to explore the parameter space" (Bayesian analysis)
   - software: KinMS, KINMS_MCMC, emcee
   - parameter: 10 free parameters; priors flat, SMBH mass flat in log between 10^4.8 and 10^9.8 Msun; M/L 0.1-4.0; final chain 10^5 steps, 10% burn-in  
  > "we ran the best chain 10$^5$ steps (with a 10% burn-in) to produce our final posterior probability distribution" (Fitting process)
   - assumption: Exponential gas disc, purely circular motion, spatially constant velocity dispersion  
  > "In this work we always assume that the gas is in circular motion" (Gas kinematics)
   - fitting: Log-likelihood from chi2 with full covariance matrix; best fit is median of the marginalised posterior; 68 and 99% CL  
  > "We use a standard logarithmic likelihood function based on the $\chi^2$ distribution" (Covariance matrix and likelihood)
   - validation: Cross-checked with KinMSpy + emcee; same best-fit values  
  > "These tests showed that our algorithm performs well, and finds the same best-fit values and parameter ranges." (Bayesian analysis)
6. **Test systematics and velocity dispersion**: Re-image at 3 km/s and refit; variable dispersion gradient; circular velocity ±10%; include AGN point source in MGE  
  > "we re-reduced our ALMA data with a channel width of 3 km s$^{-1}$" (Gas velocity dispersion)
   - software: KINMS_MCMC
   - fitting: _not stated_
   - validation: SMBH mass unchanged under ±10% velocity scaling  
  > "Despite these large changes in $M$/$L$, the SMBH mass we derive remains constant at (1.3$_{-0.14}^{+0.18}$)$\times$10$^8$ M$_{\odot}$." (Main uncertainties – Luminous mass models, AGN & dust)

## Software

- **CASA** : Imaging and uv continuum subtraction  
  > "We then used the `Common Astronomy Software Applications` (`CASA)` package to combine and image" (ALMA DATA)
- **KinMS** : Forward-model simulated cubes  
  > "We utilised the publicly available KINEMATIC MOLECULAR SIMULATION (KINMS[^3]) mm-wave observation simulation tool" (Dynamical modelling)
- **KINMS_MCMC** : MCMC fit of data cube  
  > "we used the Markov Chain Monte Carlo (MCMC) code KINMS_MCMC (Davis et al., in prep.)" (Dynamical modelling)
- **emcee** : Cross-check of the fitting code  
  > "coupled with the well tested MCMC code EMCEE" (Bayesian analysis)
- **MGE_FIT_SECTORS** : Multi-Gaussian expansion of HST image  
  > "constructed using the MGE_FIT_SECTORS package[^4]" (Gas kinematics)
- **MPFIT** : SED chi2 fitting  
  > "using the $\chi^2$ minimisation routines `MPFIT`" (Continuum emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SMBH mass | 1.3e8 | +0.18/-0.17 (99% CL, incl. AGN systematic) | Msun | 5 | (1.3$_{-0.17}^{+0.18}$) $\times$10$^8$ M$_{\odot}$ |
| i-band mass-to-light ratio | 2.14 | +0.04/-0.05 (99% CL) | Msun/Lsun | 5 | 2.14$_{-0.05}^{+0.04}$ M$_{\odot}$/L$_{\odot}$ |
| Molecular gas velocity dispersion (3 km/s cube) | 1.65 | +0.68/-0.65 (99% CL) | km/s | 6 | $\sigma_{\rm gas}$=1.65$^{+0.68}_{-0.65}$ km s$^{-1}$ |
| CO(2-1) total flux | 13.27 | 0.07 stat, 1.3 sys | Jy km/s | 2 | The total flux is 13.27 $\pm$ 0.07 $\pm$1.3 Jy km s$^{-1}$ |
| Total H2 mass | 1.62e7 | 0.01 stat, 0.36 sys | Msun | 2 | (1.62 $\pm$ 0.01 $\pm$ 0.36)$\times$10$^7$ M$_{\odot}$ |
| 1 mm continuum flux | 2.1 | 0.1 stat, 0.2 sys | mJy | 3 | total flux of 2.1 $\pm$ 0.1 $\pm$ 0.2 mJy |
| Dust mass | 2.8e5 | 0.2 stat, 1.0 sys | Msun | 3 | M$_{\rm d}$= (2.8 $\pm$ 0.2 $\pm$ 1.0)$\times10^5$ M$_{\odot}$ |
| Dust temperature | 28.7 | 0.4 | K | 3 | T$_{\rm d}$= 28.7$\pm$0.4 K |
| Figure of merit | 5.9 | not stated | dimensionless | 0 | These parameters yield $\Gamma_{\rm FOM}$ = 5.9 |
| Reduced chi2 of best model | 1.02 | not stated | dimensionless | 5 | The best model is an excellent fit ($\chi^2_{\rm red}$ = 1.02). |
| Gas disc inclination | 76.1 | -0.4/+0.5 (68%) | deg | 5 | Inclination ($^\circ$) / 72.0 / $\rightarrow$ / 89.0  / 76.1 |

## Qualitative findings

- Mm continuum is thermal dust emission, co-spatial with the gas disc.  
  > "Overall it seems that the millimetre continuum we detect is thermal in origin" (Continuum emission)

## Claim tuples

- H: Can molecular gas kinematics measure the SMBH mass in NGC4697 and agree with stellar dynamics? | E: Forward-model the ALMA CO(2-1) cube with KinMS and MCMC | R: M_BH = 1.3e8 Msun (+0.18/-0.17), versus 1.6e8 from stellar kinematics | F: Gas-based mass is consistent with stellar-kinematic measurements | **supported**
- H: Is the result robust to systematics? | E: Vary the circular velocity by ±10%, include the AGN point source, test dispersion gradients | R: M_BH unchanged for ±10% velocity scaling; point source gives 9.3e7 | F: Mass is robust, with 0.1 dex added to the error | **supported**
- H: Why is the gas velocity dispersion so low? | E: Refit the 3 km/s cube and sample GMC mass functions with Larson relations | R: sigma_gas = 1.65 km/s; random GMC draws always give >3 km/s | F: An unsampled GMC mass function partly explains it, but other mechanisms are likely needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Figure-of-merit criterion indicated the data suffice for an SMBH mass  
  > "suggesting we should be able to accurately constrain the SMBH mass in this system." (METHOD & RESULTS)
- Alternative: Working in the uv plane instead of using a covariance matrix is left for future work  
  > "In this work we take the first approach, while the latter will be explored in a future work." (Covariance matrix and likelihood)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas velocity dispersion is poorly constrained with 10 km/s channels  
  > "not well constrained given our channel width of 10 km s$^{-1}$" (Gas velocity dispersion)
- Caveat (inferred, ours): Gas mass is ignored in the mass model
- Caveat (inferred, ours): Fixed ±10% velocity scaling is arbitrary
- Caveat (inferred, ours): Unpublished MCMC code
- Caveat (inferred, ours): Distance uncertainty of ~10% scales M_BH directly
- Caveat (inferred, ours): Single short observation

## Reproducibility

- Data public (paper): ALMA programme acknowledged; HST from Hubble Legacy Archive  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00598.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: KinMS is public on GitHub; KINMS_MCMC is not released (in prep.)  
  > "publicly available KINEMATIC MOLECULAR SIMULATION (KINMS[^3])" (Dynamical modelling)
- Missing: KINMS_MCMC code
- Missing: HEART SED data
- Missing: CASA version and cleaning details
- Data volume (inferred): ~10 GB raw (single short track)
- Score (inferred): 3/5, Public data and a detailed fit description, but the MCMC code is unreleased and imaging details are sparse.
- Rediscovery candidate: no, The fitting code is unreleased, so the black hole mass cannot be reproduced exactly, though KinMS is public.

## Links

- Method: Onishi et al., 2017 (WISDOM Paper I describing the fitting tools)
- Method: (cite: 2013MNRAS.429..534D) (KinMS)
- Method: (cite: 2014MNRAS.443..911D) (Figure of merit)
- Companion: Onishi et al., 2017 (NGC3665 SMBH mass with CARMA)
- Related: WISDOM
- Related: HEART

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
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
  "facts": 84,
  "stated": 57,
  "rate": 0.679
 },
 "evidence_ok": true
}
```
