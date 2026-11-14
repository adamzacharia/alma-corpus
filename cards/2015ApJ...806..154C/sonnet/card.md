# A Disk-based Dynamical Mass Estimate for the Young Binary AK Sco

`2015ApJ...806..154C` | The Astrophysical Journal 2015 | first author: Czekala, I. | arXiv: 1505.01850 | DOI: 10.1088/0004-637X/806/2/154

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, stellar_physics
- Question: What is the dynamical mass of the AK Sco binary from its circumbinary disk CO rotation curve, and how does it compare with RV constraints and pre-MS evolutionary model predictions?  
  > "Here we report the direct determination of the AK Sco binary mass through the dynamical measurement of its circumbinary disk rotation profile using new data from ALMA." (Observations and Data Reduction)
- Target **AK Sco**: coordinates _not stated_; z/distance 142 +/- 6 pc (prior); 143.6 +/- 5.7 pc (posterior)  
  > "We adopted a Gaussian prior on $d$ based on the weighted average of these latter two measurements, with mean 142 pc and $\sigma = 6$ pc." (CO Modeling and Results); distance from weighted average of Pecaut et al. 2012 kinematic parallax (144+/-12 pc) and Anthonioz et al. 2015 (141+/-7 pc)  
  > "We adopted a Gaussian prior on $d$ based on the weighted average of these latter two measurements, with mean 142 pc and $\sigma = 6$ pc." (CO Modeling and Results)

## Data provenance

- ALMA projects: 2012.1.00496.S
- bands: Band 6 (1.3 mm)  
  > "AK Sco was observed using 32 ALMA antennas and the Band 6 receivers on 2014 April 10" (Observations and Data Reduction)
- frequencies and spectral setup: four spectral windows: CO and 13CO 2-1 with 234 MHz bandwidth and 61 kHz channels; C18O at 122 kHz; continuum window of 128 channels of 15.628 MHz  
  > "Two windows, covering the CO (230.538 GHz) and $^{13}$CO (220.399 GHz) $J$=2$-$1 transitions, spanned a 234 MHz bandwidth with 61 kHz (80 m s$^{-1}$) channels." (Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-350 m  
  > "with baseline lengths of 15–350 m" (Observations and Data Reduction)
- angular resolution: 0.75" x 0.60", P.A. = 100 deg  
  > "restored with a FWHM = $0.75\ensuremath{''}\times0.60\ensuremath{''}$ synthesized beam (with P.A. = 100$^\circ$)" (Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 45 uJy/beam; CO rms 4 mJy/beam per 0.4 km/s channel  
  > "has an RMS noise level of 45 $\mu$Jy beam$^{-1}$" (Observations and Data Reduction); "The RMS noise level at that resolution is 4 mJy beam$^{-1}$" (Observations and Data Reduction)
- time on source: observing block ~1 hour, half on AK Sco  
  > "The observing block lasted $\sim$1 hour, with half the time devoted to AK Sco." (Observations and Data Reduction)
- observing dates: 2014 April 10  
  > "Band 6 receivers on 2014 April 10" (Observations and Data Reduction)
- pi or archival as stated: program of PI Andrews  
  > "as part of program 2012.1.00496.S (PI Andrews)" (Observations and Data Reduction)
- Line: CO J=2-1 (230.538 GHz)
- Line: 13CO J=2-1 (220.399 GHz)
- Line: C18O J=2-1 (219.560 GHz)
- Other facility **Hipparcos**: trigonometric parallax used for distance discussion  
  > "A trigonometric parallax for AK Sco is available from *Hipparcos*" (CO Modeling and Results)
- External data: UBVRI photometry compilation used for SED  
  > "The $UBVRI$ photometry compilation of (cite: jensen97) was used to construct the AK Sco SED." (Comparison to Pre-MS Evolution Models) [from (cite: jensen97)]
- External data: RV constraint M sin^3 i = 2.114+/-0.010 Msun, period, mass ratio, eccentricity  
  > "a total mass constraint $M_{\ast} \sin^3{i_{\ast}} = 2.114\pm0.010$ $M_{\odot}$" (Comparison to Previous Results) [from (cite: alencar03)]
- External data: Distance estimates used for prior (144+/-12 pc; 141+/-7 pc)  
  > "Recently, (cite: anthonioz15) combined astrometric and radial velocity monitoring to estimate $d = 141\pm7$ pc." (CO Modeling and Results) [from (cite: pecaut12); (cite: anthonioz15)]
- External data: Teff = 6450+/-150 K prior from F5 classification  
  > "which we associate with $T_{\rm eff} = 6450\pm150$ K" (Comparison to Pre-MS Evolution Models) [from (cite: andersen89)]
- Simulation/model as data: BT-Settl synthetic photometry for SED; pre-MS grids of Siess, Tognelli, Dotter, Baraffe  
  > "A base parametric SED model was constructed from synthetic photometry in the BT-Settl catalog of stellar models (cite: allard03)" (Comparison to Pre-MS Evolution Models)

## Processing

### Calibration

- pipeline or manual: CASA calibration with standard Tsys/WVR, passband, gain, Titan flux scale  
  > "After applying the standard system temperature and water vapor radiometer corrections, the intrinsic passband shape was determined using the observations of J1626$-$2951 and removed." (Observations and Data Reduction)
- casa version: CASA v4.2  
  > "calibrated using the facility software package `CASA` (v4.2)" (Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "the overall amplitude scale was set using the observations of Titan" (Observations and Data Reduction)
- flux scale uncertainty: ~10% from Titan model  
  > "an additional systematic uncertainty of $\sim$10% is imposed by the absolute accuracy of the Titan emission model" (Observations and Data Reduction)
- self calibration: single iteration of phase-only self-calibration  
  > "After a single iteration of phase-only self-calibration, the reduced visibilities were time-averaged into 30 s intervals." (Observations and Data Reduction)

### Imaging

- task: CLEAN  
  > "deconvolved with the `CLEAN` algorithm" (Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Fourier inverted with natural weighting" (Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: local continuum level subtracted from line spectral windows  
  > "The local continuum level was subtracted from the spectral windows containing emission lines of interest." (Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CO averaged to 60 channels of 305 kHz (0.4 km/s)  
  > "we average these data into 60 channels of 305 kHz (0.4 km s$^{-1}$) width for further analysis" (Observations and Data Reduction)
- final beam: 0.75" x 0.60", PA 100 deg  
  > "restored with a FWHM = $0.75\ensuremath{''}\times0.60\ensuremath{''}$ synthesized beam" (Observations and Data Reduction)
- final rms: 45 uJy/beam continuum; 4 mJy/beam CO  
  > "The RMS noise level at that resolution is 4 mJy beam$^{-1}$" (Observations and Data Reduction)

### Inherited from earlier work

- Parametric 2D axisymmetric disk structure model  
  > "We adopted the two-dimensional (axisymmetric) parametric disk structure model that is described in detail by (cite: rosenfeld12)." (CO Modeling and Results) [from (cite: rosenfeld12)]
- Bayesian formalism for mapping SED posteriors to mass and age  
  > "Following the Bayesian formalism of (cite: jorgensen05), we mapped the posterior constraints from the SED modeling into an inference on {$M_{\ast}$, $\tau_{\ast}$}" (Comparison to Pre-MS Evolution Models) [from (cite: jorgensen05)]
- Molecular excitation levels calculation  
  > "calculate the corresponding molecular excitation levels (cite: pavlyuchenkov07)" (CO Modeling and Results) [from (cite: pavlyuchenkov07)]

### Not stated but needed to reproduce (our reading)

- Number, initialization and length of MCMC chains, burn-in length, and Gelman-Rubin values
- Jump covariance matrix
- Parameter prior bounds
- Outer disk radius, inner radius, and CO abundance/photodissociation treatment in the disk model
- Which channels were treated as line-free for continuum subtraction
- Phase center coordinates and the target coordinates
- Number of CLEAN iterations, mask and threshold
- Exact SED priors on the nuisance jitter terms and logg
- Details of the evolutionary grid inputs

## Analysis recipe

1. **Calibrate and image ALMA data**: CASA calibration, phase-only self-cal, 30 s averaging, continuum subtraction, natural-weighted CLEAN; CO averaged to 0.4 km/s channels  
  > "After a single iteration of phase-only self-calibration, the reduced visibilities were time-averaged into 30 s intervals." (Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Forward-model CO visibilities with disk model**: Parametric disk structure with LTE RADMC-3D ray tracing at 2.5 AU pixels, FFT and interpolation onto observed uv points, chi^2 likelihood  
  > "We then employed the `FFTW` algorithm (cite: fftw) to Fourier transform these spectral images, and then performed a band-limited interpolation of the complex visibilities onto the same spatial frequencies" (CO Modeling and Results)
   - software: RADMC-3D, FFTW
   - parameter: 12 free parameters: T10, q, Mco, rc, xi, M*, i_d, phi, offsets, vsys, d; gamma fixed to 1  
  > "The gradient parameter $\gamma$ is fixed to unity" (CO Modeling and Results)
   - assumption: LTE level populations; Keplerian rotation dominated by binary mass; vertical hydrostatic equilibrium; vertically isothermal  
  > "The bulk velocity field of the gas is assumed to be Keplerian, and dominated by the binary mass" (CO Modeling and Results)
   - fitting: MCMC with Metropolis-Hastings; uniform priors except Gaussian prior on d (142+/-6 pc); tuned jump covariance; multiple chains, Gelman-Rubin convergence  
  > "we employed the Markov Chain Monte Carlo (MCMC) technique with a Metropolis-Hastings (M-H) jump proposal." (CO Modeling and Results)
   - validation: reduced chi^2 = 1.08, image-plane residual comparison, trial fit at 122 kHz recovers same values  
  > "The reduced $\chi^2$ of the best-fit model is 1.08." (CO Modeling and Results)
3. **Compare with RV and astrometric constraints**: Convert RV M sin^3 i using disk inclination assuming co-planarity; derive dynamical distance from M/d and M sin^3 i  
  > "If we assume the gas disk and binary orbits are co-planar ($i_{\ast} = i_d$), then our constraint on $i_d$ would convert the RV constraint on the binary mass to $2.52\pm0.03$ $M_{\odot}$" (Comparison to Previous Results)
   - assumption: disk and binary co-planar  
  > "If we assume the gas disk and binary orbits are co-planar ($i_{\ast} = i_d$)" (Comparison to Previous Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **SED fit and pre-MS model mass and age**: BT-Settl SED model with extinction and per-band jitter, MCMC; then map Teff, L posterior onto four evolutionary grids  
  > "we explored the posterior distribution of ${\bm \theta}= \{ {\bm \theta}_{\rm sed}$, $\sigma_U$, $\sigma_B$, $\sigma_V$, $\sigma_R$, $\sigma_I$} conditioned on the SED data using MCMC with the ensemble sampler `emcee`" (Comparison to Pre-MS Evolution Models)
   - software: emcee
   - parameter: Teff prior 6450+/-150 K; d prior 142+/-6 pc  
  > "which we associate with $T_{\rm eff} = 6450\pm150$ K" (Comparison to Pre-MS Evolution Models)
   - assumption: identical binary components; solar metallicity; Fitzpatrick reddening with R_V=4.3; near-IR excluded  
  > "We assumed the components of the AK Sco binary are identical." (Comparison to Pre-MS Evolution Models)
   - fitting: emcee ensemble sampler with Gaussian priors on d and Teff  
  > "we imposed simple Gaussian priors on $d$ (as in Sect. 3) and $T_{\rm eff}$." (Comparison to Pre-MS Evolution Models)
   - validation: comparison with dynamical mass  
  > "These model-predicted masses are consistent, but are all $\sim$1.5–2 $\sigma$ higher than the dynamical mass inferred from the ALMA data." (Comparison to Pre-MS Evolution Models)

## Software

- **CASA** v4.2: calibration and imaging  
  > "calibrated using the facility software package `CASA` (v4.2)" (Observations and Data Reduction)
- **RADMC-3D** : radiative transfer and ray tracing of model disk  
  > "propagating synthetic photons through the model structure with the `RADMC-3D` radiative transfer code" (CO Modeling and Results)
- **FFTW** : Fourier transform of model images  
  > "We then employed the `FFTW` algorithm (cite: fftw) to Fourier transform these spectral images" (CO Modeling and Results)
- **emcee** : SED MCMC  
  > "using MCMC with the ensemble sampler `emcee` (cite: foreman-mackey13)" (Comparison to Pre-MS Evolution Models)
- **triangle.py** : corner plot figure  
  > "Figure [\[fig:triangle\]](#fig:triangle) was generated with `triangle.py` (cite: foreman-mackey14)." (Acknowledgments)
- **Julia** : programming language for analysis  
  > "This research made extensive use of the Julia programming language (cite: julia12) and Astropy (cite: astropy13)." (Acknowledgments)
- **Astropy** : general use  
  > "This research made extensive use of the Julia programming language (cite: julia12) and Astropy (cite: astropy13)." (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Binary dynamical mass | 2.49 | 0.10 | Msun | 2 | $M_\ast$ ($M_\odot$)              / 2.49  / 0.10 |
| M*/d | 0.01731 | 0.00015 | Msun/pc | 2 | $M_{\ast}/d = 0.01731\pm0.00015$ $M_{\odot}$ pc$^{-1}$ |
| Disk inclination | 109.4 | 0.5 | deg | 2 | $i_d$ (${}^\circ$)                         / 109.4 / 0.5 |
| Characteristic radius | 14.3 | 1.2 | AU | 2 | $r_c$ (AU)                        / 14.3  / 1.2 |
| Dynamical distance | 145.5 | 2.0 | pc | 3 | we derive a dynamical distance to the system of $d=145.5 \pm 2.0$ pc |
| Continuum flux density at 1.3 mm | 32.65 | 0.07 (+~10% systematic) | mJy | 1 | a total flux density of $32.65\pm0.07$ mJy |
| CO 2-1 integrated intensity | 2.21 | 0.01 | Jy km/s | 1 | has an integrated intensity of $2.21\pm0.01$ Jy km s$^{-1}$ |
| Pre-MS model mean mass | 2.68 | 0.03 | Msun | 4 | $M_{\ast} = 2.68\pm0.03$ $M_{\odot}$ and $\tau_{\ast} = 18\pm1$ Myr |
| Age from pre-MS models | 18 | 1 | Myr | 4 | $M_{\ast} = 2.68\pm0.03$ $M_{\odot}$ and $\tau_{\ast} = 18\pm1$ Myr |
| Stellar Teff from SED | 6365 | 155 | K | 4 | We found $T_{\rm eff} = 6365\pm155$ K |

## Qualitative findings

- Disk is compact (rc ~14 AU) with ~5-10 MJup of gas and dust, detected in continuum, CO, 13CO and C18O  
  > "A relatively compact disk in orbit around the AK Sco binary, with $\sim$5–10 $M_{\rm Jup}$ of gas and dust" (Summary and Conclusions)
- Eccentric disk ruled out: e_d < 0.04 at 99.7% confidence  
  > "with $e_d < 0.04$ (at 99.7% confidence)" (Comparison to Previous Results)

## Claim tuples

- H: Can a disk rotation-curve fit give an accurate binary mass? | E: Forward model CO 2-1 visibilities with RADMC-3D and MCMC | R: M* = 2.49+/-0.10 Msun, consistent with RV-derived 2.52+/-0.03 Msun if coplanar | F: Disk-based dynamical mass method is validated | **supported**
- H: Do pre-MS evolutionary models reproduce the dynamical mass? | E: SED fit and mapping onto four model grids | R: Models give 2.60-2.71 Msun, 1.5-2 sigma above dynamical mass, age 18+/-1 Myr | F: Models are marginally consistent but systematically high by 7-10% | **partially**
- H: Is the ALMA mass consistent with the interferometric/astrometric mass of Anthonioz et al.? | E: Compare inclinations and masses | R: Their M*=2.80+/-0.11 Msun is a 2 sigma discrepancy | F: Minor tension, possibly from warp or ring model simplicity | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Disk rotation provides dynamical mass independent of evolutionary models and workable for single stars  
  > "it is the *only* method capable of performing that task for *single* stars." (Comparison to Previous Results)
- Alternative: Eccentric disk model explored; significant eccentricity ruled out  
  > "We also explored an eccentric disk model" (Comparison to Previous Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass uncertainty dominated by distance prior  
  > "where the uncertainty is dominated by the distance prior" (CO Modeling and Results)
- Limitation (authors): Disk model assumes axisymmetry; warps could bias  
  > "The difference between $i_\textrm{ring}$ and $i_d$ might be explained with a warp in the disk structure" (Comparison to Previous Results)
- Caveat (inferred, ours): Parametric disk model may be biased by warps or non-Keplerian motion
- Caveat (inferred, ours): Mass is linear in distance and the prior mixes two uncertain measurements
- Caveat (inferred, ours): SED fit relies on Teff prior and variability handling
- Caveat (inferred, ours): Metropolis-Hastings convergence details sparse

## Reproducibility

- Data public (paper): ALMA project data acknowledged; code open source  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00496.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: Analysis code open source (MIT) at github.com/iancze/JudithExcalibur  
  > "The code used to perform the analysis described here is open source and freely available under an MIT license at <https://github.com/iancze/JudithExcalibur>." (CO Modeling and Results)
- Missing: MCMC chain settings and priors bounds
- Missing: CLEAN parameters and line-free channels
- Missing: Jitter priors and evolutionary grid details
- Data volume (inferred): ~5-20 GB for one 1-hour execution block
- Score (inferred): 4/5, Single public dataset, open code and clearly specified model; some MCMC and imaging settings are missing.
- Rediscovery candidate: yes, Public ALMA data, open code, numeric headline result (M*=2.49 Msun).

## Links

- Method: (cite: rosenfeld12) (disk structure model and technique)
- Method: (cite: jorgensen05) (Bayesian mass and age inference)
- Companion: (cite: anthonioz15) (VLTI constraints on inner disk and inclination)
- Companion: (cite: alencar03) (RV orbital solution)
- Related: Upper Centaurus-Lupus association

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
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
  "facts": 82,
  "stated": 59,
  "rate": 0.72
 },
 "evidence_ok": true
}
```
