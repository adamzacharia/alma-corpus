# exoALMA. XVI. Predicting Signatures of Large-scale Turbulence in Protoplanetary Disks

`2025ApJ...984L..21B` | The Astrophysical Journal Letters 2025 | first author: Barraza-Alfaro, Marcelo | arXiv: 2504.19853 | DOI: 10.3847/2041-8213/adc42d

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: What observational signatures would large-scale flows driven by the VSI, MRI and GI produce in exoALMA-quality 12CO(3-2) observations?  
  > "We aim to predict the observational signatures of such large-scale flows, as they would appear in high-resolution Atacama Large Millimeter/submillimeter Array observations of CO rotational lines" (abstract)
- Target **Synthetic disk models (VSI, MRI, GI)**: coordinates _not stated_; z/distance 140 pc  
  > "we assumed a distance to the source of $140$ pc (cite: Teague_exoALMA)" (3.1 Radiative Transfer Setup); distance from Teague_exoALMA  
  > "we assumed a distance to the source of $140$ pc (cite: Teague_exoALMA)" (3.1 Radiative Transfer Setup)

## Data provenance

- ALMA projects: 2021.1.01123.L
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (≈345.796 GHz)
- External data: Parametric gas temperature structure (T_atm0=24.68 K, T_mid0=14.3 K, q=-0.371, Z_q0=70 au) from the DM Tau fiducial model  
  > "$T_{\rm atm0} = 24.68$ K, $T_{\rm mid0} = 14.3$ K, $q=-0.371$, and $Z_{\rm q0}=70$ au" (3.1 Radiative Transfer Setup) [from Flaherty2020]
- External data: Mean exoALMA 12CO emission radius R95 = 411 au and typical Z/R ~0.27  
  > "is $411$ au for the exoALMA sample (cite: Galloway_exoALMA)" (3.2 Synthetic exoALMA observations) [from Galloway_exoALMA]
- Simulation/model as data: Three 3D global simulations run with PLUTO: RHD (VSI) from Flock2020, non-ideal MHD (MRI) D2G_e-2 from Flock2015, SGHD (GI) M5B10 from Bethune2021; one snapshot each  
  > "we analyzed an individual simulation snapshot for each of the studied instabilities taken after the disk had reached a quasi-steady state" (2 Methods for Numerical Simulations)

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
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Spectral rebinning to 104 m/s with CASA imrebin  
  > "we binned the raw data cubes in frequency down to a velocity resolution of $104 \rm \,m\,s^{-1}$ using CASA" (3.2 Synthetic exoALMA observations)
- final beam: 35 mas circular Gaussian (synthetic)  
  > "we consider a Gaussian beam with a FWHM of $35$ mas" (3.2 Synthetic exoALMA observations)
- final rms: ~0.16 mJy/beam after convolution (white noise added)  
  > "resulting in an RMS of $\sim 0.16$ mJy beam $^{-1}$ after convolution" (3.2 Synthetic exoALMA observations)

### Inherited from earlier work

- Radiative transfer framework analogous to the exoALMA benchmark  
  > "The adopted framework is analogous to the exoALMA benchmark, presented and validated in (cite: Bae_exoALMA)." (3 Methods for Radiative Transfer Models) [from Bae_exoALMA]
- Modified Keplerian rotation profile with mass component  
  > "The modified Keplerian disk rotation profile includes an additional radial-dependent component that can account for super-Keplerian or sub-Keplerian deviations from a purely Keplerian disk (cite: Teague2022)." (3.3 Line Analysis Tools) [from Teague2022]

### Not stated but needed to reproduce (our reading)

- Which simulation snapshot/output number was used for each instability
- Initial emission surface parameter values for the eddy fit
- Noise realization/seed and exact synthetic channel width and number of channels
- bettermoments clipping/masking settings
- Raw simulation data availability
- Radiative transfer photon number and dust opacity settings

## Analysis recipe

1. **Run or adopt 3D (M)HD simulations**: Use existing PLUTO simulations of VSI, MRI, GI disks; one snapshot each  
  > "We post-processed outputs from three 3D global (magneto-)hydrodynamic simulations, one representative of each of the disk instabilities explored." (2 Methods for Numerical Simulations)
   - software: PLUTO
   - fitting: _not stated_
   - validation: _not stated_
2. **Radiative transfer of 12CO(3-2)**: RADMC-3D ray tracing of upper hemisphere only, with parametric temperature, CO freeze-out and photodissociation, five inclinations 5-60 deg, 26 m/s channels  
  > "We computed images for five disk inclinations ranging from $i=5^{\circ}$ to $i=60^{\circ}$" (3.1 Radiative Transfer Setup)
   - software: RADMC-3D, fargo2radmc3d
   - parameter: 12CO/H2 = 1e-4; freeze-out below 21 K (factor 1e-5); photodissociation below 1e21 cm^-2 (factor 1e-5)  
  > "reducing the CO number density by a factor $10^{-5}$ in regions where the gas temperature falls below $21$ K" (3.1 Radiative Transfer Setup)
   - parameter: PA = 90 deg, distance 140 pc  
  > "We assumed a disk position angle $\rm PA$ of $90^{\circ}$ east of north" (3.1 Radiative Transfer Setup)
   - assumption: Same parametric temperature profile for all models  
  > "For simplicity and to have the same temperature structure for all disk models, we assumed a parametric temperature profile" (3.1 Radiative Transfer Setup)
   - fitting: _not stated_
   - validation: _not stated_
3. **Make synthetic exoALMA-like cubes**: Rebin to 104 m/s, add white noise, convolve with 35 mas beam  
  > "Before convolving the images with the Gaussian beam, we include noise in our models as white noise" (3.2 Synthetic exoALMA observations)
   - software: CASA
   - assumption: 35 mas beam keeps ~40 beams across disk like exoALMA at 150 mas for 411 au disks  
  > "roughly $\sim 40$ beams across the disk diameter" (3.2 Synthetic exoALMA observations)
   - fitting: _not stated_
   - validation: _not stated_
4. **Extract line centroid, width and peak maps**: bettermoments percentiles method: median gives centroid, half 16-84 percentile range gives width; peak for temperature  
  > "the median returns the line centroid, and the half of the range between the 16th and 84th percentile returns an accurate line width measurement" (3.3 Line Analysis Tools)
   - software: bettermoments
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit background rotation and compute residuals**: eddy MCMC fit of modified Keplerian model with elevated surface to centroid maps; subtract model; GoFish azimuthal average subtraction for width and peak  
  > "We set 80 walkers initialized with the disk radiative transfer input model parameters for $M_{\star}$ and $M_{\rm disk}$" (Eddy disk model and fitting procedure)
   - software: eddy, GoFish, emcee
   - parameter: 2000 burn-in steps plus 4000 sampling steps; r_in=20 au, r_out=100 au; PA fixed, vLSR=0, distance 140 pc  
  > "We set 2000 steps for the walkers to burn in, and 4000 additional to sample the posterior distribution." (Eddy disk model and fitting procedure)
   - fitting: emcee MCMC; free: M_star, z0, psi, R_taper, q_taper, i, M_disk, gamma, x0, y0; priors not stated  
  > "The free parameters in our calculations are $M_{\star}$, the emission surface parameters" (Eddy disk model and fitting procedure)
   - validation: Compared with ideal residuals from a model with the bulk rotation subtracted in the input velocity  
  > "we generated a radiative transfer model in which we subtract the disk rotation in the input azimuthal velocity" (5.1 Kinematic signatures in the raw images)

## Software

- **PLUTO** 4.2 (RHD simulation): Numerical simulations  
  > "The simulation was conducted with PLUTO version 4.2" (2.1 VSI-unstable disk simulation)
- **RADMC-3D** 2.0: Monte-Carlo radiative transfer  
  > "RADMC-3D[^2] (cite: Dullemond2012) version 2.0" (3 Methods for Radiative Transfer Models)
- **CASA** : imrebin spectral rebinning  
  > "using CASA[^4] `imrebin` task" (3.2 Synthetic exoALMA observations)
- **bettermoments** : Collapsing cubes to centroid, width, peak  
  > "we used the Python package BETTERMOMENTS" (3.3 Line Analysis Tools)
- **eddy** : Modified Keplerian disk fit  
  > "We used EDDY to obtain the best fit modified Keplerian disk model" (3.3 Line Analysis Tools)
- **GoFish** : Azimuthal-average subtraction for width and peak maps  
  > "we used GOFISH to subtract the disk azimuthal average" (3.3 Line Analysis Tools)
- **emcee** : MCMC sampling in eddy  
  > "MCMC sampling implemented with the `emcee` package" (Eddy disk model and fitting procedure)
- **fargo2radmc3d** : Basis for building RADMC-3D inputs from PLUTO outputs  
  > "We build our RADMC-3D input files using scripts based in FARGO2RADMC3D" (3 Methods for Radiative Transfer Models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Average RMS velocity perturbation at Z~2.5H, VSI | 29 | not stated | m/s | 1 | are $29 \, \rm  m\,s^{-1}$, $111 \, \rm m\,s^{-1}$ and $\rm 142\, m\,s^{-1}$, for the VSI, the MRI and the GI, respectively |
| Average RMS velocity perturbation at Z~2.5H, MRI | 111 | not stated | m/s | 1 | are $29 \, \rm  m\,s^{-1}$, $111 \, \rm m\,s^{-1}$ and $\rm 142\, m\,s^{-1}$, for the VSI, the MRI and the GI, respectively |
| Average RMS velocity perturbation at Z~2.5H, GI | 142 | not stated | m/s | 1 | are $29 \, \rm  m\,s^{-1}$, $111 \, \rm m\,s^{-1}$ and $\rm 142\, m\,s^{-1}$, for the VSI, the MRI and the GI, respectively |
| VSI gas density contrast within annuli at Z=2.5H (median) | ≈15 | not stated | percent | 1 | has a median value of $\approx 15\%$ (computed within $35$ and $85$ au) |
| Decrease in RMS velocity from 2.5H to 1.5H (VSI, MRI, GI) | ~47, ~62, ~18 | not stated | percent | 1 | shows a decrease of $\sim 47 \%$ for the VSI, $\sim 62 \%$ for the MRI, while only $\sim 18 \%$ for GI |
| GI-driven spiral residual magnitude in synthetic centroid maps | ~100 | not stated | m/s | 5 | reaching magnitudes of $\sim 100$ m s$^{-1}$ |

## Qualitative findings

- VSI gives quasi-axisymmetric rings/arcs in centroid residuals at low inclination, losing symmetry above ~30-45 deg; MRI and GI give spirals; MRI can create localized planet-like features in one layer  
  > "We predict that the MRI can induce localized kinematic signatures in mid-inclination disks." (Summary and Conclusions)
- V4046 Sgr and PDS 66 outer regions appear nearly laminar  
  > "These results indicate that V4046 Sgr and PDS 66 have nearly laminar outer regions." (6.1 Turbulence signatures in exoALMA disks)

## Claim tuples

- H: Are large-scale VSI, MRI and GI perturbations detectable at exoALMA resolution? | E: Synthetic 12CO(3-2) cubes with 35 mas beam, 104 m/s channels and noise, analyzed with eddy residuals | R: Ring, arc and spiral residuals remain resolved | F: Large-scale perturbations from all three are detectable by exoALMA-quality data | **supported**
- H: Does the exoALMA sample show VSI signatures? | E: Qualitative comparison of predictions with exoALMA residuals | R: Few ring/arc structures, none robust | F: No robust case of VSI in outer disks yet | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Single simulation snapshots with particular parameters; no Hall effect or ambipolar diffusion; no embedded planets; limited 20-100 au range  
  > "our unstable disks simulations are for particular sets of parameters, which control the resulting strength of the instabilities." (4 Results from Numerical Simulations)
- Caveat (inferred, ours): Comparison with exoALMA data is only qualitative
- Caveat (inferred, ours): Beam of 35 mas is chosen ad hoc to mimic number of beams
- Caveat (inferred, ours): Single snapshot per instability and fixed temperature structure
- Caveat (inferred, ours): Simplified CO chemistry affects emission height and temperature residuals

## Reproducibility

- Data public (paper): Acknowledgments cite ALMA data ADS/JAO.ALMA#2021.1.01123.L, but the results use synthetic data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.1.01123.L." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Simulation snapshot outputs
- Missing: Snapshot numbers
- Missing: bettermoments and eddy initial/prior settings
- Missing: RADMC-3D photon counts and dust opacities
- Data volume (inferred): Simulation outputs of several GB; no ALMA data required
- Score (inferred): 3/5, Codes are public and parameters are largely given, but simulation snapshots and several settings are missing.
- Rediscovery candidate: no, Results are from synthetic data and mostly qualitative; simulation outputs are not stated as public.

## Links

- Method: Bae_exoALMA (Benchmark framework for post-processing and kinematic analysis)
- Method: Teague2022 (Modified Keplerian model)
- Companion: Teague_exoALMA (exoALMA survey overview)
- Companion: Izquierdo_exoALMA (Residual and kinematic analysis of exoALMA disks)
- Companion: Galloway_exoALMA (Emission surfaces and temperature structure)
- Related: exoALMA Large Program

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 35,
  "rate": 0.443
 },
 "evidence_ok": true
}
```
