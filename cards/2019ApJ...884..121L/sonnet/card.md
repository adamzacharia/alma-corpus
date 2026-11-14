# A Reverse Shock in GRB 181201A

`2019ApJ...884..121L` | The Astrophysical Journal 2019 | first author: Laskar, Tanmoy | arXiv: 1907.13128 | DOI: 10.3847/1538-4357/ab40ce

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: transients
- Question: Can the radio/mm SED of GRB 181201A be decomposed into reverse-shock and forward-shock components, and what do they imply for the jet Lorentz factor, magnetization and environment?  
  > "Our observations present the first time that a single radio-frequency spectral energy distribution can be decomposed directly into RS and forward shock (FS) components." (abstract)
- Target **GRB 181201A**: coordinates RA 21h17m11.20s, Dec -12d37m50.9s (J2000, Swift/XRT)  
  > "RA = $21^{\rm h}17^{\rm m}11{\rlap.}^{\rm 
s}$20, Dec = -12$^\circ$ 37$'$ 50.9$''$ (J2000)" (2.1 X-ray: Swift/XRT); "Spectroscopic observations with the Very Large Telescope at the European Southern Observatory yielded a redshift of $z=0.450$ based on identification of the Mg II doublet" (2 Observations and Data Analysis); z/distance z=0.450  
  > "RA = $21^{\rm h}17^{\rm m}11{\rlap.}^{\rm 
s}$20, Dec = -12$^\circ$ 37$'$ 50.9$''$ (J2000)" (2.1 X-ray: Swift/XRT); "Spectroscopic observations with the Very Large Telescope at the European Southern Observatory yielded a redshift of $z=0.450$ based on identification of the Mg II doublet" (2 Observations and Data Analysis); distance from VLT spectroscopy, Mg II doublet (GCN)  
  > "RA = $21^{\rm h}17^{\rm m}11{\rlap.}^{\rm 
s}$20, Dec = -12$^\circ$ 37$'$ 50.9$''$ (J2000)" (2.1 X-ray: Swift/XRT); "Spectroscopic observations with the Very Large Telescope at the European Southern Observatory yielded a redshift of $z=0.450$ based on identification of the Mg II doublet" (2 Observations and Data Analysis)

## Data provenance

- ALMA projects: 2018.1.01454.T
- bands: Band 3 (3 mm), 5 epochs, 0.88 to 29.8 days  
  > "We obtained 5 epochs of ALMA Band 3 (3 mm) observations of GRB 181201A spanning 0.88 days to 29.8 days after the burst" (2.3 Millimeter: ALMA)
- frequencies and spectral setup: two 4 GHz base-bands centered at 91.5 and 103.5 GHz (first epoch), 90.4 and 102.4 GHz (later epochs)  
  > "The observations utilized two 4 GHz-wide base-bands centered at 91.5 and 103.5 GHz, respectively, in the first epoch, and at 90.4 and 102.4 GHz in subsequent epochs." (2.3 Millimeter: ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PI program (PI: Laskar)  
  > "through program 2018.1.01454.T (PI: Laskar)" (2.3 Millimeter: ALMA)
- Other facility **VLA**: 1.2-37 GHz cm-band afterglow light curves to ~164 d (programs 18A-088, 18B-407)  
  > "We detected and tracked the flux density of the afterglow from 1.2 GHz to 37 GHz over multiple epochs until $\approx164$ d after the burst." (2.4 Centimeter: VLA)
- Other facility **uGMRT**: Band 4 (550 MHz) and Band 5 (1450 MHz) observations at 12.5 and 13.5 d, program 35_065  
  > "starting 12.5 d and 13.5 d after the burst in Bands 4 (center frequency 550 MHz) and 5 (center frequency 1450 MHz), respectively" (2.5 Meter: uGMRT)
- Other facility **Swift XRT/UVOT**: X-ray and UV light curves  
  > "XRT continued observing the afterglow for $20$ d in photon counting mode." (2.1 X-ray: Swift/XRT)
- Other facility **MASTER, GROND, MDM, Liverpool Telescope**: optical/NIR photometry from 150 s onward  
  > "We present our combined optical and NIR data set in Table [2]" (2.2 UV, optical, and near-IR)
- External data: Konus-Wind prompt spectrum (Band fit, fluence)  
  > "The time-averaged *Konus*-Wind spectrum in the 20 keV–10 MeV energy range can be fit with a Band model" (2 Observations and Data Analysis) [from (cite: gcn23495)]
- External data: redshift z=0.450 from VLT spectroscopy  
  > "yielded a redshift of $z=0.450$ based on identification of the Mg II doublet" (2 Observations and Data Analysis) [from (cite: gcn23488)]
- External data: optical photometry from GCN circulars  
  > "We also collected all optical photometry for this event published in GCN circulars." (2.2 UV, optical, and near-IR) [from GCN circulars]

## Processing

### Calibration

- pipeline or manual: CASA analysis; bandpass/flux calibrators J2258-2758, J2148+0657 or J2000-1748; gain calibrator J2131-1207  
  > "One of J2258-2758, J2148+0657, and J2000-1748 was used for bandpass and flux density calibration, while J2131-1207 was used for complex gain calibration in all epochs." (2.3 Millimeter: ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: one round of phase-only self-cal in first two ALMA epochs  
  > "We performed one round of phase-only self-calibration in the first two epochs, where the deconvolution residuals indicated the presence of phase errors." (2.3 Millimeter: ALMA)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Likelihood function and modeling procedure  
  > "Further details of the modeling procedure, including the likelihood function employed, are described elsewhere" (4.1 Markov Chain Monte Carlo Analysis) [from (cite: lbz+13; lbt+14; lab+16)]
- Synchrotron spectra computed with weighting prescription for smooth light curves  
  > "We compute the resulting synchrotron spectra using the weighting prescription described in (cite: lbt+14) to generate smooth light curves at all observed frequencies." (3 Basic Considerations) [from (cite: lbt+14)]
- Lorentz factor consistency equations and energy balance argument  
  > "by solving the following equations self-consistently (cite: zkm03; lab+18) at the deceleration time" (4.2 Determination of Ejecta Initial Lorentz Factor) [from (cite: zkm03; lab+18)]

### Not stated but needed to reproduce (our reading)

- MCMC priors other than nu_m,r > 1e8 Hz
- tclean parameters: weighting, robust, cell, image size, masking
- flux density extraction method (point-source fit vs. image peak) for ALMA/VLA
- CASA version
- self-calibration solution intervals
- likelihood treatment of upper limits and systematic errors
- host-galaxy contribution parametrization
- ALMA flux scale uncertainty

## Analysis recipe

1. **Fit radio/mm SED and light curves**: Smoothly broken power law to 3.9 d SED; power-law fits to ALMA, X-ray, UV light curves  
  > "The feature spans 3–24 GHz, and can be fit with a smoothly broken power law" (3.1 Radio/mm: presence of additional component)
   - fitting: _not stated_
   - validation: _not stated_
2. **Determine circumburst density profile**: Compare ISM vs wind closure relations with optical/X-ray SED, break frequency and decay rates  
  > "The observed decay rate in the *Swift*/UVOT $uvw2$-band and in ground-based optical $r^{\prime}$-band observations at $\approx0.2$–8.7 days is $\alpha_{\rm UV} = 
-1.21\pm0.02$, consistent with the wind case" (3.2 Circum-burst density profile)
   - assumption: p≈2; wind medium k=2  
  > "We therefore focus on the wind environment in the remainder of this article." (3.2 Circum-burst density profile)
   - fitting: _not stated_
   - validation: _not stated_
3. **Joint RS+FS MCMC fit**: Fit all X-ray to radio data with FS and non-relativistic RS model in wind medium plus host contribution  
  > "we fit all available X-ray to radio observations with a model comprising an FS and RS produced by a relativistic jet propagating in a wind-like circum-burst environment" (4.1 Markov Chain Monte Carlo Analysis)
   - software: emcee
   - parameter: 512 walkers, 10k steps, burn-in ≲0.15%  
  > "We ran 512 walkers for 10k steps and discarded a few ($\lesssim0.15\%$) initial non-converged steps with low log likelihood as burn-in." (4.1 Markov Chain Monte Carlo Analysis)
   - assumption: RS reference time 0.01 d  
  > "all at a reference time, $t_{\rm ref}\equiv0.01$ days" (4.1 Markov Chain Monte Carlo Analysis)
   - fitting: emcee ensemble sampler; free parameters p, E_K,iso, A*, eps_e, eps_B, A_V, nu_a,r, nu_m,r, nu_c,r, F_nu,m,r, g  
  > "We performed a Markov Chain Monte Carlo (MCMC) exploration of the multi-dimensional parameter space using `emcee`" (4.1 Markov Chain Monte Carlo Analysis)
   - validation: Best-fit model compared with light curves and SEDs  
  > "fits the X-ray to radio light curves and radio SEDs well" (4.1 Markov Chain Monte Carlo Analysis)
4. **Derive t_dec, R_B and Gamma_0**: Invert RS/FS consistency relations for t_dec and R_B; Gamma_0 from energy-balance with Sedov length, for all MCMC samples  
  > "We compute $\ensuremath{\Gamma_{0}}$ for all MCMC samples using equation [\[eq:Gammajet\]]" (4.2 Determination of Ejecta Initial Lorentz Factor)
   - assumption: Simplified treatment, point source on line of sight, R = 2 Gamma0^2 c t_dec/(1+z)  
  > "For a point source moving along the line of sight, this radius corresponds to the deceleration time given by, $R = 2\ensuremath{\Gamma_{0}}^2 c \ensuremath{t_{\rm dec}}/(1+z)$" (4.2 Determination of Ejecta Initial Lorentz Factor)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : ALMA, VLA and GMRT data reduction  
  > "We analyzed the data using the Common Astronomy Software Application (cite: mws+07)" (2.3 Millimeter: ALMA)
- **emcee** : MCMC sampling  
  > "using `emcee` (cite: fhlg13)" (4.1 Markov Chain Monte Carlo Analysis)
- **uvotproduct** v2.4: UVOT aperture photometry  
  > "with the uvotproduct (v2.4) software" (2.2 UV, optical, and near-IR)
- **Photutils** : Liverpool Telescope aperture photometry  
  > "We performed aperture photometry using the Astropy Photutils package (cite: bsr+16)" (2.2 UV, optical, and near-IR)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| initial Lorentz factor Gamma_0 | 103 | +10/-8 | dimensionless | 4 | resulting in $\ensuremath{\Gamma_{0}}= 103^{+10}_{-8}$ |
| relative magnetization R_B | 0.64 | +0.07/-0.08 | dimensionless | 4 | $\ensuremath{R_{\rm B}}=0.64^{+0.07}_{-0.08}$ from the MCMC |
| log t_dec | -2.27 | +0.13/-0.14 | log days | 4 | $\log(\ensuremath{t_{\rm dec}}/{\rm days})=-2.27^{+0.13}_{-0.14}$ |
| ALMA light curve decay rate | -0.71 | 0.01 | dimensionless | 1 | $\alpha_{\rm ALMA}=-0.71\pm0.01$ |
| RS spectral peak frequency at 3.9 d | 5.5 | 0.4 | GHz | 1 | $\nu_{\rm 
peak}=5.5\pm0.4$ GHz |
| RS Lorentz factor | 1.97 | +0.08/-0.07 | dimensionless | 4 | $\bar{\Gamma}_{\rm 
RS}=1.97^{+0.08}_{0.07}$ |
| FS electron index p | 2.11 | 0.01 | dimensionless | 3 | $2.11\pm0.01$ |

## Qualitative findings

- Radio SED at 3.9 d shows two components, interpreted as RS (low-frequency) and FS; wind-like environment favored.  
  > "The radio and millimeter SED at 3.9 days clearly exhibits two distinct components." (3.1 Radio/mm: presence of additional component)

## Claim tuples

- H: The 3.9 d radio/mm bump is reverse-shock emission | E: SED decomposition and joint RS+FS MCMC modeling | R: RS+FS model fits data with mildly relativistic RS, Gamma_0=103, R_B=0.64 | F: Reverse shock detected; ejecta weakly magnetized | **supported**
- H: Low-density environments favor RS detectability | E: Derived A* and compared with other RS events | R: A*≈0.02, low | F: Supports hypothesis | **supported**
- H: Alternative models (two-component jet, thermal electrons) explain the bump | E: Cold electron model comparison | R: Thermal model does not match the cm data as well; two-component jet cannot be confirmed or ruled out | F: RS model preferred | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: ISM environment rejected; two-jet and thermal-electron scenarios considered  
  > "Indeed, all cm-band light curves are inconsistent with this extrapolation, and thus inconsistent with an ISM-like environment." (3.2 Circum-burst density profile)
- How they decided it was enough: _not stated_
- Limitation (authors): Gamma_0 not directly constrained due to nu_m,r–F_nu,m,r degeneracy; FS degeneracies; mm excess and late X-ray excess unexplained.  
  > "Therefore, we can constrain $\ensuremath{t_{\rm dec}}$ and $\ensuremath{R_{\rm B}}$ through this system of equations, but not $\ensuremath{\Gamma_{0}}$." (4.2 Determination of Ejecta Initial Lorentz Factor)
- Caveat (inferred, ours): Gamma_0 relies on a simplified energy-balance estimate
- Caveat (inferred, ours): RS parameter g≈2.7 exceeds theoretical expectation
- Caveat (inferred, ours): KN corrections not included
- Caveat (inferred, ours): non-relativistic RS formulas applied to mildly relativistic RS

## Reproducibility

- Data public (paper): Full data tables said to be available online; ALMA data from program 2018.1.01454.T  
  > "This is a sample of the full table available on-line." (Table 1)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: MCMC priors and likelihood details
- Missing: model code (from earlier papers)
- Missing: flux extraction method
- Data volume (inferred): ~10-50 GB for ALMA Band 3 5 epochs; VLA/GMRT additional
- Score (inferred): 4/5, ALMA flux tables and posteriors given, but imaging settings, priors and model code are not specified; modeling inherited from earlier papers.
- Rediscovery candidate: no, Main results come from a custom afterglow model with inherited, unreleased code and incomplete settings.

## Links

- Method: (cite: lbt+14) (afterglow model and weighting prescription)
- Method: (cite: lbz+13) (RS+FS modeling procedure and likelihood)
- Method: (cite: zkm03) (RS/FS consistency relations)
- Companion: (cite: lab+18) (GRB 161219B, earlier ALMA RS case)

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 37,
  "rate": 0.487
 },
 "evidence_ok": true
}
```
