# Characterization of Ring Substructures in the Protoplanetary Disk of HD 169142 from Multiwavelength Atacama Large Millimeter/submillimeter Array Observations

`2019ApJ...881..159M` | The Astrophysical Journal 2019 | first author: Macías, Enrique | arXiv: 1907.07277 | DOI: 10.3847/1538-4357/ab31a2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Are the multiple rings of the HD 169142 disk produced by accumulations of large dust grains (dust traps), and what are the radial profiles of optical depth, temperature, beta and grain size distribution?  
  > "A simple parametric model is used to estimate the radial profile of the dust optical depth, temperature, density, and particle size distribution." (abstract)
- Target **HD 169142**: coordinates _not stated_; z/distance 113.6±0.8 pc  
  > "the nearby (d=$113.6\pm0.8$ pc; (cite: gai18; bai18)) Herbig Ae star HD 169142" (Introduction); distance from Gaia (cite: gai18; bai18)  
  > "the nearby (d=$113.6\pm0.8$ pc; (cite: gai18; bai18)) Herbig Ae star HD 169142" (Introduction)

## Data provenance

- ALMA projects: 2016.1.01158.S, 2012.1.00799.S, 2015.1.00490.S, 2015.1.01301.S
- bands: Band 3 (new), Band 6 and Band 7 (archival)  
  > "We present new ALMA observations obtained at Band 3 (project code: 2016.1.01158.S), as well as archival ALMA data at Band 7" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-41 m minimum baselines listed per execution  
  > "2017 September 09 | 25.4 | 40 | 41" (Table 1)
- angular resolution: Band 7 0.12x0.09 arcsec; Band 6 0.12x0.08 arcsec; Band 3 0.22x0.10 arcsec  
  > "$0\rlap.''22\times0\rlap.''10$, PA$=-88^{\circ}$" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: rms 0.16 (B7), 0.08 (B6), 0.017 (B3) mJy/beam  
  > "| 3 | 97.493 | 3.08 | $0\rlap.''22\times0\rlap.''10$, PA$=-88^{\circ}$ | 0.017 | $18.29\pm0.17$ |" (Table 2)
- time on source: _not stated_
- observing dates: Band 7 2015 Jul-Aug; Band 6 2016 Sep; Band 3 2017 May and Sep  
  > "2017 September 09" (Table 1)
- pi or archival as stated: _not stated_
- Other facility **Gaia**: Position and proper motion used to align epochs  
  > "in combination with the position and proper motions measured by Gaia (cite: gai18)" (Observations)
- External data: Disk inclination 13±1 deg and PA 5±5 deg used for priors and profiles  
  > "($i=13\pm1^{\circ}$ and PA$=5\pm5^{\circ}$; (cite: ram06))" (Visibility Modeling) [from (cite: ram06)]
- External data: DSHARP dust opacities and Python tools for kappa and beta vs amax and p  
  > "Using the absorption opacities and Python tools provided by (cite: bir18)" (Dust Surface Density and Particle Size Distribution) [from (cite: bir18)]
- External data: Gas mass of 19 MJ used for dust-to-gas ratio  
  > "(cite: fed17) estimated a gas mass of $19$ M$_J$." (Dust Surface Density and Particle Size Distribution) [from (cite: fed17)]
- External data: Stellar luminosity 10 Lsun  
  > "Assuming $L_{\star}=10~L_{\odot}$ (cite: fed17)" (Model Results) [from (cite: fed17)]
- External data: Freezing temperature ranges of CO2, CO, N2, H2O  
  > "We take the ranges of freezing temperature of CO$_2$, CO, N$_2$, and H$_2$O from (cite: zha15)." (Snowlines) [from (cite: zha15)]

## Processing

### Calibration

- pipeline or manual: Archive reduction scripts, then self-calibration  
  > "The raw data were calibrated using the reduction scripts provided in the ALMA archive and their corresponding version of `CASA`" (Observations)
- casa version: CASA 5.3.0 for further calibration and imaging  
  > "Further calibration and imaging was performed in `CASA` version 5.3.0." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1924-2914, Pallas, J1733-1304 depending on execution  
  > "| 2015 08 Aug | 41.4 | 43 | 35 | 331.040 | Pallas | J1924-2914 | J1826-2924 |" (Table 1)
- flux scale uncertainty: ~10% Band 7, ~5% Band 6  
  > "($\sim10\%$ and $\sim5\%$ at Band 7 and 6, respectively)" (Observational Results)
- self calibration: Phase self-cal with solint 120 s down to 10 s, then amplitude self-cal; peak SNR improved 5-10x (Band 3 10-20%)  
  > "Phase self-calibration was first performed iteratively decreasing the solution interval in each step, from 120 s to 10 s" (Observations)

### Imaging

- task: tclean with mtmfs, nterms=2  
  > "using the `mtmfs` algorithm with $nterms=2$ and multiple scales at 0, 1, 3, and 5 times the beam size" (Observations)
- deconvolver: _not stated_
- weighting robust: Uniform for Band 7 and 6; Briggs robust=0.0 for Band 3  
  > "uniform weighting for Band 7 and 6, and Briggs weighting (robust$=0.0$) for Band 3" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: 0, 1, 3, 5 times the beam size  
  > "multiple scales at 0, 1, 3, and 5 times the beam size" (Observations)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: All datasets per band combined; Band 6+7 imaged together for spectral index  
  > "the Band 7 and Band 6 data were combined and imaged together in `tclean` using `mtmfs`" (Observations)
- smoothing: _not stated_
- final beam: see angular resolution  
  > "$0\rlap.''12\times0\rlap.''08$, PA$=71^{\circ}$" (Table 2)
- final rms: 0.16, 0.13, 0.08, 0.017 mJy/beam (B7, B6+7, B6, B3)  
  > "| 6+7 | 288.755 | 1.04 | $0\rlap.''11\times0\rlap.''08$, PA$=63^{\circ}$ | 0.13 | $369\pm2$ |" (Table 2)

### Inherited from earlier work

- Disk substructure notation B1-B4, D1-D4  
  > "we will follow the notation by (cite: per19) and we will refer to the disk substructures as “B" (for bright annular substructures" (Observational Results) [from (cite: per19)]
- Visibility modeling approach (axisymmetric, Hankel transform)  
  > "Following studies of other protoplanetary disks (cite: zha16; pin18; mac18), we assume that the disk emission is axisymmetric" (Visibility Modeling) [from (cite: zha16; pin18; mac18)]

### Not stated but needed to reproduce (our reading)

- Binning details for the 2000 deprojected visibility bins (uniform in what)
- Initial walker positions and prior ranges for most flat priors
- Imaging mask, image size, cell size, number of clean iterations and thresholds
- Self-calibration reference model/solint per dataset and flagging
- Exact Band 6+7 spectral windows and continuum channel selection
- Which uv-range/weights used for the visibility fit
- Burn-in or convergence criteria for 100,000-iteration MCMC
- Prior ranges for dust grain model fit

## Analysis recipe

1. **Calibrate and self-calibrate**: Archive scripts, phase then amplitude self-calibration per dataset  
  > "each dataset was separately self-calibrated with the continuum emission" (Observations)
   - software: CASA, tclean
   - parameter: solint 120 s to 10 s; amplitude: mtmfs nterms=2, scales=0, natural weighting  
  > "assuming a linear spectrum ($nterms=2$) and point-like components ($scales=0$), as well as using natural weighting" (Observations)
   - fitting: _not stated_
   - validation: peak SNR improvement  
  > "self-calibration resulted in substantial improvements of the peak SNR, typically by factors between 5 and 10" (Observations)
2. **Align epochs and image**: Correct proper motions with fixvis/fixplanets to 2016 Sep 14, image each band with mtmfs  
  > "all datasets were corrected for their proper motions and shifted to the first epoch of the Band 6 observations (2016 Sep 14)" (Observations)
   - software: CASA, fixvis, fixplanets, tclean
   - fitting: _not stated_
   - validation: _not stated_
3. **Radial profiles and spectral index map**: Average in concentric ellipses with i=13 deg, PA=5 deg; alpha map from Band 6+7 mtmfs; median in ellipses  
  > "These profiles were obtained by averaging the emission within concentric ellipses, projected with the inclination and PA of the disk" (Observational Results)
   - software: CASA
   - parameter: Band 3 profile from two 90 deg cones N and S  
  > "the profile at this band is calculated using only two $90^{\circ}$ cones to the North and South" (Observational Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit multiwavelength visibilities with parametric model**: Fit real part of deprojected visibilities with I=B(Td)(1-exp(-tau)); power-law Td, tau0 and beta base plus three asymmetric Gaussian rings  
  > "we aim at fitting an analytical model of the radial intensity profile of the disk to the real part of the observed deprojected visibilities" (Visibility Modeling)
   - software: EMCEE
   - parameter: 51 free parameters; 2000 bins; 200 walkers, 100,000 iterations; 5 frequencies  
  > "We used 200 walkers and ran 100,000 iterations" (Visibility Modeling)
   - assumption: Geometrically thin, vertically isothermal, absorption opacity only, nu0=345 GHz, r0=10 au, axisymmetric  
  > "we assume that the disk is geometrically thin and vertically isothermal" (Visibility Modeling)
   - fitting: Affine-invariant ensemble MCMC; Gaussian priors on flux systematics (10% B7, 5% B6/B3), offsets (~5% of resolution), i=13±1, PA=5±5; flat priors elsewhere; beta limited to 0.2-3.1; ring width lower limit ~0.01 arcsec  
  > "we set a flat prior that limits $\beta$ to be between 0.2 and 3.1 at all radii" (Visibility Modeling)
   - validation: Residual images; chains converged; also tested four-ring model  
  > "our model successfully reproduces the observations in great detail" (Model Results)
5. **Derive dust surface density, amax and p**: At each radius MCMC fit of tau0 and beta profiles with DSHARP opacities, free Sigma_d, amax, p  
  > "using $\Sigma_d$, $a_{max}$, and $p$ as the three free parameters at each radius" (Dust Surface Density and Particle Size Distribution)
   - software: dsharp_opac, MCMC
   - parameter: 50 walkers, 10000 iterations, burn-in 8000  
  > "For each radius we run an MCMC with 50 walkers for 10000 iterations, with a burn-in phase of 8000 iterations." (Dust Surface Density and Particle Size Distribution)
   - assumption: DSHARP dust composition, power-law size distribution n(a)~a^-p  
  > "We use the dust composition employed in the DSHARP ALMA Large Program (cite: bir18)" (Dust Surface Density and Particle Size Distribution)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.3.0: Calibration, self-calibration, imaging  
  > "`CASA` (v5.3.0; (cite: mcm07))" (Software)
- **tclean** : Imaging with hogbom and mtmfs  
  > "The `hogbom` algorithm within the `tclean` task was used for the imaging during the phase-only self-calibration" (Observations)
- **fixvis/fixplanets** : Proper-motion correction and shift to common epoch  
  > "the `CASA` tasks `fixvis` and `fixplanets` were used" (Observations)
- **EMCEE** : MCMC sampling of visibility model  
  > "We use the MCMC ensemble samplers with affine invariance (cite: goo10) in the `EMCEE` package (cite: for13)." (Visibility Modeling)
- **dsharp_opac** : Opacities and Python tools for kappa and beta  
  > "Using the absorption opacities and Python tools provided by (cite: bir18)" (Dust Surface Density and Particle Size Distribution)
- **Numpy, Matplotlib, Astropy** : General analysis and plotting  
  > "`Numpy` (cite: van11), `Matplotlib` (cite: hun07), `Astropy` (cite: ast18)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Flux density Band 3 (3.08 mm, r<0.9 arcsec) | 18.29 | 0.17 | mJy | 2 | $18.29\pm0.17$ |
| Flux density Band 7 (0.886 mm) | 554 | 2 | mJy | 2 | $554\pm2$ |
| Flux density Band 6 (1.33 mm) | 166.2 | 1.3 | mJy | 2 | $166.2\pm1.3$ |
| Temperature at 10 au, T0 | 77 | +2/-2 | K | 4 | reference temperature at 10 au of $77^{+2}_{-2}$ K |
| Temperature power-law index q | -0.501 | +0.011/-0.011 | dimensionless | 4 | a power $-0.501^{+0.011}_{-0.011}$ |
| Ring 1 radius x | 0.2288 | +0.0021/-0.0007 | arcsec | 4 | $0\rlap.''2288^{+0\rlap.''0021}_{-0\rlap.''0007}$ |
| Ring 2 (B2/3) radius | 0.5474 | +0.0014/-0.0009 | arcsec | 4 | $0\rlap.''5474^{+0\rlap.''0014}_{-0\rlap.''0009}$ |
| Ring 3 (B4) radius | 0.631 | +0.003/-0.002 | arcsec | 4 | $0\rlap.''631^{+0\rlap.''003}_{-0\rlap.''002}$ |
| Ring 1 beta peak decrement b(1) | -1.22 | +0.06/-0.04 | dimensionless | 4 | $-1.22^{+0.06}_{-0.04}$ |
| Ring 1 tau0 amplitude | 0.63 | +0.02/-0.02 | dimensionless | 4 | $0.63^{+0.02}_{-0.02}$ |
| Best-fit inclination and PA (max likelihood) | ~12.3 deg and ~4.8 deg | not stated | deg | 4 | The inclination and PA of the model with maximum likelihood are $\sim12.3^{\circ}$ and $\sim4.8^{\circ}$ |
| B1 size distribution slope p | 1.509 | +0.014/-0.006 | dimensionless | 5 | $p=1.509^{+0.014}_{-0.006}$ |
| B1 maximum grain size | 4.85 | +0.15/-0.15 | mm | 5 | $a_{max}=4.85^{+0.15}_{-0.15}$ mm |
| B1 dust surface density | 0.89 | +0.04/-0.04 | g cm^-2 | 5 | $\Sigma_d \sim0.89^{+0.04}_{-0.04}$ g cm$^{-2}$ |
| Total dust mass | 160 | +250/-90 | Earth masses | 5 | we estimate a total dust mass of $160^{+250}_{-90}$ M$_{\bigoplus}$ |
| Dust-to-gas mass ratio | 0.03 | +0.04/-0.02 | dimensionless | 5 | dust-to-gas mass ratio of $0.03^{+0.04}_{-0.02}$ |
| Underestimate of peak optical depth from clean images | ~3 | not stated | dimensionless | 4 | significant underestimation of the peak optical depths by a factor $\sim3$ |

## Qualitative findings

- Rings show increases in tau coupled with decreases in beta, indicating accumulations of large grains; gaps have ISM-like p.  
  > "our model finds that the multiple rings in HD 169142 can only be explained with increases in $\tau$ coupled with substantial decreases in $\beta$." (Model Results)
- Snowlines of main volatiles do not coincide with B1 and B2/3; planet-disk interaction favored.  
  > "our multi-wavelength analysis indicates that at least the most prominent substructures in HD 169142 (B1 and B2/3) are not associated with snowlines." (Snowlines)

## Claim tuples

- H: Rings are dust traps with large grain accumulation rather than just optical depth increases | E: Joint visibility fit at 0.89, 1.3, 3 mm with tau0 and beta rings | R: Rings have increased tau0 and decreased beta; amax ~1 cm in rings, flatter p | F: Rings trace accumulations of large particles, probably in pressure bumps | **supported**
- H: Inner ring could host conditions for the streaming instability | E: Fit of Sigma_d, amax and p with DSHARP opacities | R: B1 p=1.509, Sigma_d~0.89 g/cm2, dust-to-gas ~1 | F: B1 may trigger streaming instability | **partially**
- H: Snowlines or MHD effects explain the rings | E: Compared fitted temperature profile to snowline locations and MHD predictions | R: Main snowlines are not at the rings; B4 may be near CO snowline | F: Planet-disk interaction is the most likely origin | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Visibility-domain fitting avoids differing uv coverage and resolution among bands  
  > "we perform our analysis in the visibility domain" (Observational Results)
- Alternative: Four-ring model did not reproduce the triple outer ring; three-ring used  
  > "our model with four rings does not reproduce the triple ring morphology of the outer disk" (Visibility Modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): Finite resolution smears tau and beta; peak optical depths are lower limits  
  > "the peak optical depths estimated by our model are in principle lower limits" (Optical Depth)
- Limitation (authors): Scattering neglected and dust composition assumed  
  > "we have made the common assumption that the main source of opacity is the absorption opacity, without considering the scattering component" (Visibility Modeling)
- Caveat (inferred, ours): Three free parameters per radius for two observables in the dust-size fit is degenerate
- Caveat (inferred, ours): Results depend on assumed DSHARP composition and neglect scattering
- Caveat (inferred, ours): Band 3 beam is very elongated and amplitude calibration errors can bias beta
- Caveat (inferred, ours): Only 3 rings fit despite known 4 rings

## Reproducibility

- Data public (paper): Archival and new data cited by ALMA project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00799.S, JAO.ALMA#2015.1.00490.S, JAO.ALMA#2015.1.01301.S, and JAO.ALMA#2016.1.01158.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Custom visibility-fitting code not released
- Missing: Binning scheme and many priors
- Missing: Image sizes, masks and cleaning thresholds
- Data volume (inferred): ~50-150 GB raw across 4 projects
- Score (inferred): 3/5, Data public and recipe fairly detailed with numeric results, but the custom fitting code and several settings are not given.
- Rediscovery candidate: no, Requires writing a custom multi-band visibility MCMC fitter with unstated binning and priors.

## Links

- Method: (cite: bir18) (DSHARP dust opacities and tools)
- Method: (cite: mac18) (Similar visibility modeling approach)
- Companion: (cite: per19) (High-resolution ALMA data resolving outer ring into three rings; substructure notation)
- Companion: (cite: ber18) (First report of Band 7 data)
- Related: DSHARP

## Checks

```json
{
 "quotes": 79,
 "quotes_ok": 79,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 54,
  "rate": 0.651
 },
 "evidence_ok": true
}
```
