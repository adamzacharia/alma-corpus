# ALMA continuum observations of the protoplanetary disk AS 209. Evidence of multiple gaps opened by a single planet

`2018A&A...610A..24F` | Astronomy and Astrophysics 2018 | first author: Fedele, D. | arXiv: 1711.05185 | DOI: 10.1051/0004-6361/201731978

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What is the dust surface density structure of the AS 209 disk gaps and rings, and can planet-disk interaction (single or two planets, low viscosity) explain them?  
  > "This paper presents new ALMA 1.3 mm continuum observations of the T Tauri disk AS 209 where axisymmetric gaps and rings are detected." (Introduction)
- Target **AS 209**: coordinates RA 16h49m15.296s, Dec -14d22m09.02s (J2000)  
  > "The ALMA observations of AS 209 (J2000: R.A. = 16$^{\rm{h}}$49$^{\rm{m}}$15.296$^{\rm{s}}$, DEC = –14$^\circ$22$\ensuremath{'}$09.02$\ensuremath{''}$)" (2 Observations and Data reduction); "is part of the young (age $\sim 0.5 - 1.0\,$Myr (cite: Natta06)) Ophiuchus star forming region at a distance of 126 pc from the Sun (cite: Brown16)." (Introduction); z/distance 126 pc  
  > "The ALMA observations of AS 209 (J2000: R.A. = 16$^{\rm{h}}$49$^{\rm{m}}$15.296$^{\rm{s}}$, DEC = –14$^\circ$22$\ensuremath{'}$09.02$\ensuremath{''}$)" (2 Observations and Data reduction); "is part of the young (age $\sim 0.5 - 1.0\,$Myr (cite: Natta06)) Ophiuchus star forming region at a distance of 126 pc from the Sun (cite: Brown16)." (Introduction); distance from Gaia Collaboration (Brown16)  
  > "The ALMA observations of AS 209 (J2000: R.A. = 16$^{\rm{h}}$49$^{\rm{m}}$15.296$^{\rm{s}}$, DEC = –14$^\circ$22$\ensuremath{'}$09.02$\ensuremath{''}$)" (2 Observations and Data reduction); "is part of the young (age $\sim 0.5 - 1.0\,$Myr (cite: Natta06)) Ophiuchus star forming region at a distance of 126 pc from the Sun (cite: Brown16)." (Introduction)

## Data provenance

- ALMA projects: 2015.1.00486.S
- bands: Band 6 (211–275 GHz), 1.3 mm continuum  
  > "in band 6 (211–275 GHz)" (2 Observations and Data reduction)
- frequencies and spectral setup: one broad 2 GHz spectral window centered at 230 GHz  
  > "The correlator setup includes a broad (2 GHz bandwidth) spectral window centered at 230 GHz." (2 Observations and Data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.19" x 0.14" (PA = 75.5 deg), uniform weighting  
  > "which yields a synthesised beam of 0.19$''$ $\times$ 0.14$''$ (PA = 75.5$^{\circ}$)" (2 Observations and Data reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 0.1 mJy/beam; peak 13 mJy/beam  
  > "The peak flux is 13 mJy beam$^{-1}$ and the r.m.s. is 0.1 mJy beam$^{-1}$." (2 Observations and Data reduction)
- time on source: 40 minutes per execution block  
  > "totalling 40 minutes, per block, on-source" (2 Observations and Data reduction)
- observing dates: 2016 September 22 (38 antennas) and 26 (41 antennas)  
  > "have been performed on 2016 September 22 (with 38 antennas) and 26 (41 antennas)" (2 Observations and Data reduction)
- pi or archival as stated: PI D. Fedele, project 2015.1.00486.S  
  > "as part of the project ID 2015.1.00486.S (PI: D. Fedele)" (2 Observations and Data reduction)
- External data: Stellar mass 0.9 Msun, K5, L=1.5 Lsun  
  > "AS 209 ($M_{\star} = 0.9\,M_{\odot}$, spectral type K5, $L_{\star} = 1.5\,L_{\odot}$, (cite: Tazzari16))" (Introduction) [from (cite: Tazzari16)]
- External data: Critical scale height h_c=0.13 and flaring psi=0.1  
  > "The critical scale height ($h_{\rm c}=0.13$) and disk flaring ($\psi=0.1$) are taken from (cite: Andrews11)." (4.1 Model description) [from (cite: Andrews11)]
- External data: Dust mass absorption coefficients  
  > "The dust mass absorption coefficients are taken from (cite: Andrews11)." (4.1 Model description) [from (cite: Andrews11)]
- External data: s_max = 2000 micron from multi-frequency analysis  
  > "In this paper we fix $s_{\rm max} = 2000\,$$\mu$m in agreement with the multi-frequency continuum analysis of AS 209 by (cite: Tazzari16)." (4.1 Model description) [from (cite: Tazzari16)]
- Simulation/model as data: DALI radiative transfer grid of dust surface density models, and FARGO-3D 2D planet-disk simulations with dust, used for comparison  
  > "we have run 2D simulations of planet-disk interaction using a version of FARGO-3D (cite: Benitez16) modified to include dust dynamics (cite: Rosotti16)." (5 Comparison to hydrodynamical simulations)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7 (stated for imaging)  
  > "The continuum image was created using CASA.CLEAN (CASA version 4.7)" (2 Observations and Data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1517-2422 bandpass; J1733-1304 phase and flux (text garbled)  
  > "Calibration was done with $J1517-2422$ as bandpass calibrator, $J1733-1304$ as phase and flux the flux calibrator." (2 Observations and Data reduction)
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration on 233 GHz continuum TDM spw, reference antenna DA41; data time binned to 60 s  
  > "Self-calibration was performed using the 233 GHz continuum TDM spectral window with DA41 as the reference antenna." (2 Observations and Data reduction)

### Imaging

- task: CASA clean  
  > "The continuum image was created using CASA.CLEAN (CASA version 4.7)" (2 Observations and Data reduction)
- deconvolver: _not stated_
- weighting robust: uniform weighting, chosen after trying different schemes  
  > "after trying different weighting schemes, we opted for a uniform weight" (2 Observations and Data reduction)
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
- final beam: 0.19" x 0.14", PA 75.5 deg  
  > "which yields a synthesised beam of 0.19$''$ $\times$ 0.14$''$ (PA = 75.5$^{\circ}$)" (2 Observations and Data reduction)
- final rms: 0.1 mJy/beam  
  > "the r.m.s. is 0.1 mJy beam$^{-1}$" (2 Observations and Data reduction)

### Inherited from earlier work

- Dust settling prescription with two grain populations  
  > "dust settling is included following (cite: dAlessio06), i.e., adopting two power-law grain size populations with different scale heights" (4.1 Model description) [from (cite: dAlessio06)]
- Gap width vs planet mass relation used to estimate planet mass  
  > "Starting from the relationship between the width of a gap opened by a planet and its mass derived by (cite: Rosotti16)" (5 Comparison to hydrodynamical simulations) [from (cite: Rosotti16)]

### Not stated but needed to reproduce (our reading)

- Exact self-calibration solution intervals and number of iterations
- Clean mask, threshold, cell and image size
- Whether the flux calibrator is J1733-1304 and flux scale uncertainty
- Visibility fit radial grid and GALARIO setup details; parameter initialization of walkers
- Gap-profile weights treatment and uv binning for plots
- DALI stellar spectrum and radiation field details; gas-to-dust ratio and T structure
- FARGO-3D planet mass growth/time of snapshots and boundary conditions, dust-to-gas ratio
- Pipeline vs manual calibration

## Analysis recipe

1. **Image the continuum**: CASA clean with uniform weighting after self-calibration  
  > "after trying different weighting schemes, we opted for a uniform weight which yields a synthesised beam of 0.19$''$ $\times$ 0.14$''$ (PA = 75.5$^{\circ}$)." (2 Observations and Data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit axisymmetric brightness profile to visibilities**: Tapered power-law with piecewise scaling factors for gaps/rings; synthetic visibilities via GALARIO; chi2 on visibilities  
  > "we use the GALARIO library (cite: Tazzari17b) to compute the synthetic visibilities (by sampling the Fourier transform of the model image in all the observed $(u,v)$-points)" (3.1 Characterization of the brightness profile)
   - software: emcee, GALARIO
   - parameter: 80 chains, 45000 steps after 5000 burn-in  
  > "sampled with 80 chains for 45000 steps (after 5000 burn-in steps)" (3.1 Characterization of the brightness profile)
   - assumption: axisymmetry; flat priors  
  > "We assume flat priors for all the free parameters." (3.1 Characterization of the brightness profile)
   - fitting: Goodman & Weare ensemble MCMC in emcee, posterior exp(-chi2/2), median and half 16-84% interval  
  > "for each parameter, we estimate its value as the median of the marginalized distribution and its uncertainty as half the interval between 16% and 84% percentiles." (3.1 Characterization of the brightness profile)
   - validation: Chain convergence; deprojected synthetic visibilities match observed up to 1500 klambda  
  > "the deprojected synthetic visibilities match the observed ones up to 1500k$\lambda$." (3.1 Characterization of the brightness profile)
3. **Derive dust surface density with radiative transfer grid**: DALI models over grid of dust mass, gamma1, gamma2 and scaling factors; images converted to visibilities with simobserve; chi2 on deprojected binned visibilities; iterative grid refinement  
  > "The fiducial model is defined by the set of parameters that minimize the $\chi^2$ between the observed and synthetic visibilities (eq. [\[eq:chi\]](#eq:chi)) within the explored parameter space." (4.2 Fiducial model)
   - software: DALI, CASA simobserve
   - parameter: bin size 30 klambda; s_max=2000 micron; p=3.5; chi=0.2; f_large=0.85  
  > "after deprojecting and binning the visibilities (bin size of 30 k$\lambda$)" (4.2 Fiducial model)
   - assumption: distance 126 pc, Mstar 0.9, fixed geometry i=35, PA=86  
  > "$i$ \[$^{\circ}$\]             | 35" (Table of fixed parameters)
   - fitting: Grid search chi2 minimisation, multi-step  
  > "In a second step, we constrain the values of the scaling factors while keeping fixed $M_{\rm dust}, \gamma_1, \gamma_2$." (4.2 Fiducial model)
   - validation: _not stated_
4. **Compare with planet-disk hydrodynamical simulations**: 2D FARGO-3D with dust, one or two planets, viscous alpha=1e-4 and inviscid; compare gap width/depth/location with inferred surface density  
  > "The simulations were run using a logarithmic radial grid, extending from 10 au to 300 au at a resolution of $Nr \times N\phi = 550 \times 1024$." (5 Comparison to hydrodynamical simulations)
   - software: FARGO-3D
   - parameter: T=190(R/100au)^-0.55, Sigma_gas=7.5(R/100au)^-1, grain size 1 mm, alpha 0 or 1e-4  
  > "Gas Surface Density | $7.5 (R/100\,\mathrm{au})^{-1}$" (Table 2)
   - fitting: No exhaustive fit  
  > "we have not conducted an exhaustive fit to the data" (5 Comparison to hydrodynamical simulations)
   - validation: _not stated_

## Software

- **CASA** 4.7: calibration, clean imaging, simobserve  
  > "The continuum image was created using CASA.CLEAN (CASA version 4.7)" (2 Observations and Data reduction)
- **emcee** : MCMC fit of visibilities  
  > "implemented in the EMCEE package (cite: Foreman13)" (3.1 Characterization of the brightness profile)
- **GALARIO** : synthetic visibilities  
  > "we use the GALARIO library (cite: Tazzari17b)" (3.1 Characterization of the brightness profile)
- **DALI** : dust radiative transfer disk model  
  > "we use the dust radiative transfer code implemented into the thermo-chemical disk model DALI" (4 Analysis with a physical disk model)
- **FARGO-3D** : planet-disk hydrodynamical simulations with dust  
  > "using a version of FARGO-3D (cite: Benitez16) modified to include dust dynamics (cite: Rosotti16)" (5 Comparison to hydrodynamical simulations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Gap 1 center | 61.7 | 0.5 | au | 2 | $R_{G1}$ \[au\]      /   0 /  80 /    61.7 $\pm$ 0.5 / |
| Gap 2 center | 103.2 | 0.4 | au | 2 | $R_{G2}$ \[au\]      /  80 / 110 /   103.2 $\pm$ 0.4 / |
| Gap 1 half width | 8.0 | 0.2 | au | 2 | $hw_{G1}$ \[au\]     /   0 /  30 /     8.0 $\pm$ 0.2 / |
| Gap 2 half width | 15.6 | 0.2 | au | 2 | $hw_{G2}$ \[au\]     /   0 /  30 /    15.6 $\pm$ 0.2 / |
| delta_G1 | 0.03 | 0.005 | dimensionless | 2 | $\delta_{G1}$        /   0 /   1 /  0.03 $\pm$ 0.005 / |
| delta_G2 | 0.025 | 0.005 | dimensionless | 2 | $\delta_{G2}$        /   0 /   1 / 0.025 $\pm$ 0.005 / |
| Inclination | 35.3 | 0.8 | deg | 2 | $i$ \[$^\circ$\]     /   0 /  90 /    35.3 $\pm$ 0.8 / |
| Position angle | 86.0 | 0.7 | deg | 2 | $PA$ \[$^\circ$\]    /   0 / 180 /    86.0 $\pm$ 0.7 / |
| Fiducial dust mass | 3.5e-4 | not stated | Msun | 3 | $M_{\rm dust}$ \[$M_{\odot}$\] / $1 \cdot 10^{-4}$ / $5 \cdot 10^{-4}$ / $0.5 \cdot 10^{-4}$ / $3.5 \cdot 10^{-4}$ |
| Outer planet mass | 0.2 MJ (0.67 Msaturn) at 95 au | not stated | MJ | 4 | Saturn-like ($M_{\rm planet} = 0.2 M_{\rm J} = 0.67\,M_{\rm Saturn}$) planet at $r = 95\,$au |

## Qualitative findings

- Inner gap partially filled with mm grains while outer gap is largely devoid; a possible unresolved gap near 20-30 au  
  > "the inner gap is partially filled with millimeter grains while the outer gap is largely devoid of dust." (abstract)

## Claim tuples

- H: Can a single low-viscosity planet open both gaps? | E: FARGO-3D inviscid and alpha=1e-4 runs with planet at 95 au | R: Inviscid 0.2 MJ planet reproduces both gaps; alpha=1e-4 too shallow | F: Single Saturn-mass planet with alpha<1e-4 is consistent with the structure | **supported**
- H: Is a second inner planet allowed? | E: Added inner planet at 57 au | R: Masses up to ~0.1 MJ compatible | F: Inner planet possible but not required | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Alpha=1e-4 viscous case rejected as gaps too shallow  
  > "even a modest viscosity $\alpha = 10^{-4}$ is too high to produce deep enough gaps to explain the structures in AS 209" (5 Comparison to hydrodynamical simulations)
- How they decided it was enough: _not stated_
- Limitation (authors): No exhaustive fit of hydrodynamical simulations  
  > "Given the relative expense of the hydrodynamic simulations, we have not conducted an exhaustive fit to the data" (5 Comparison to hydrodynamical simulations)
- Caveat (inferred, ours): Dust opacity and s_max fixed; surface density depends on these
- Caveat (inferred, ours): Planet mass degenerate with viscosity and gas density assumptions
- Caveat (inferred, ours): Grid search without uncertainties on DALI parameters

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Self-calibration details
- Missing: Clean parameters
- Missing: FARGO-3D setup details and DALI configuration
- Data volume (inferred): ~20-50 GB for two Band 6 execution blocks
- Score (inferred): 3/5, Project code and fit setup given, but imaging/selfcal details and hydro setup incomplete.
- Rediscovery candidate: no, Main results need DALI/FARGO-3D runs with incomplete setup, though the visibility fit is redoable.

## Links

- Method: (cite: Tazzari17b) (GALARIO visibility modelling)
- Method: (cite: Rosotti16) (FARGO-3D with dust and gap-width planet mass relation)
- Companion: (cite: Tazzari16) (multi-frequency AS 209 analysis)
- Companion: (cite: Huang16) (C18O image of AS 209)

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
  "facts": 75,
  "stated": 46,
  "rate": 0.613
 },
 "evidence_ok": true
}
```
