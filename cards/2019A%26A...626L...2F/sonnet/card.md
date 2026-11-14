# High gas-to-dust size ratio indicating efficient radial drift in the mm-faint CX Tauri disk

`2019A&A...626L...2F` | Astronomy and Astrophysics 2019 | first author: Facchini, S. | arXiv: 1905.09204 | DOI: 10.1051/0004-6361/201935496

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: How compact is the mm dust disk of CX Tau relative to its CO gas disk, and does it show substructure, indicating radial drift?  
  > "CX Tau is a good target that can be used to characterize the gas and dust properties (in particular the radial extent) of a compact continuum protoplanetary disk" (Introduction)
- Target **CX Tau**: coordinates _not stated_; z/distance 127.9±0.7 pc  
  > "CX Tau is an M2.5 star, located at $127.9\pm0.7\,$pc from the Sun" (Introduction); distance from Gaia (Gaia Collaboration 2016, 2018)  
  > "CX Tau is an M2.5 star, located at $127.9\pm0.7\,$pc from the Sun" (Introduction)

## Data provenance

- ALMA projects: 2016.1.00715.S
- bands: 1.3 mm (Band 6)  
  > "significantly higher angular resolution ALMA data of CX Tau at 1.3 mm" (Introduction)
- frequencies and spectral setup: seven spectral windows; 12CO at 61 kHz (0.079 km/s) resolution  
  > "The spectral setup had seven spectral windows" (2 Observations and data reduction)
- continuum bandwidth: 2661 MHz  
  > "The total bandwidth for the continuum results in $2661\,$MHz." (2 Observations and data reduction)
- arrays: _not stated_
- configurations: C40-5 and C40-8  
  > "CX Tau was observed in two configurations (C40-5 and C40-8) on 2016 November 5 and 2017 September 25, respectively" (2 Observations and data reduction)
- baselines: 18-1124 m (compact); 41-14851 m (extended)  
  > "The compact configuration spanned baselines between 18 and 1124 m, while the extended configuration ranged between 41 and 14851 m." (2 Observations and data reduction)
- angular resolution: 55x32 mas continuum; 0.17''x0.13'' CO  
  > "The resulting synthesized beam is $55\times32\,$mas, with a position angle (P.A.) of $13.6^\circ$." (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: 20.3 uJy/beam continuum; 4.4 mJy/beam per 0.1 km/s channel CO  
  > "The rms noise level is $\sim20.3\,\mu$Jy beam$^{-1}$." (2 Observations and data reduction)
- time on source: 20 and 54 minutes  
  > "with on-source integration times of 20 and 54 minutes" (2 Observations and data reduction)
- observing dates: 2016 Nov 5 and 2017 Sep 25  
  > "on 2016 November 5 and 2017 September 25, respectively" (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz (spw centre))
- External data: Stellar mass 0.31 Msun (dynamical)  
  > "The dynamical estimate for the mass of the star is $0.31\,M_\odot$" (Introduction) [from (cite: 2017ApJ...844..158S)]
- External data: Lupus gas-to-dust ratio at 90% radius: 1.96 ± 0.04  
  > "they found that the typical ratio is $1.96$, with a standard error on the mean of $0.04$" (3.2 Radial extent of CO) [from (cite: 2018ApJ...859...21A)]
- External data: Unresolved spectral index 1-3 mm of 2.3  
  > "The unresolved spectral index between 1 and 3  mm is $2.3$" (3.3 Continuum intensity profile) [from (cite: 2010A&A...512A..15R)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7  
  > "The data were calibrated using the `CASA` package, version 4.7" (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800 (C40-5); J0238+1636 (C40-8)  
  > "In the C40-8 configuration, the same calibrator was used for bandpass, whereas J0238+1636 was used as flux calibrator." (2 Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: phase and amplitude; solints scan length and 120 s (compact), scan length and 360 s (extended)  
  > "with solution intervals equal to the scan length and 120 s for the compact configuration data, and to the scan length and 360 s for the extended configuration data" (2 Observations and data reduction)

### Imaging

- task: CASA clean; concat to merge  
  > "Images in the sky plane were produced using the `clean` task." (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: continuum Briggs robust 0.5; CO robust 2.0  
  > "The best compromise between angular resolution and S/N with the continuum data is with a Briggs robust weighting of 0.5." (2 Observations and data reduction)
- uv taper: 0.1'' taper for CO  
  > "the line was imaged with a Briggs robust weighting of 2.0, and an additional $0.1\ensuremath{''}$ taper" (2 Observations and data reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: continuum excludes channels within ±60 km/s of targeted lines  
  > "excluding all channels within $\pm 60\,$km s$^{-1}$ from the targeted lines" (2 Observations and data reduction)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CO rebinned to 0.1 km/s channels  
  > "the data were re-binned into $0.1\,$km s$^{-1}$ channels" (2 Observations and data reduction)
- final beam: 55x32 mas PA 13.6 deg (continuum); 0.17''x0.13'' PA 23.5 deg (CO)  
  > "The restoring beam is $0.17\ensuremath{''}\times0.13\ensuremath{''}$, with a P.A. of $23.5^\circ$." (2 Observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- Azimuthally averaged CO intensity profile and curve-of-growth method  
  > "the azimuthally averaged intensity profile is computed, as in (cite: 2018ApJ...859...21A)" (3.2 Radial extent of CO) [from (cite: 2018ApJ...859...21A)]
- Mid-plane temperature profile and flaring angle 0.02  
  > "$\varphi$ is the flaring angle, which we set equal to $0.02$ as in (cite: 2018ApJ...869L..42H)" (3.3 Continuum intensity profile) [from (cite: 2018ApJ...869L..42H)]

### Not stated but needed to reproduce (our reading)

- Number of clean iterations, threshold and masks
- Cell and image size
- Which ALMA calibrator flux values were adopted and flux scale uncertainty
- Self-calibration reference antenna and the number of iterations
- Exact continuum uv-fit initial conditions and the uv-binning
- Details of flux-density radii error computation

## Analysis recipe

1. **Fit continuum visibilities**: Azimuthally symmetric two-component intensity profile fitted in uv-plane with GALARIO and MCMC  
  > "the disk is modeled in the $uv$-plane assuming azimuthal symmetry. To do so, we use the GALARIO code" (3.1 Radial extent of continuum)
   - software: GALARIO, emcee
   - parameter: 90 walkers, 18000 steps after 2000 burn-in; uniform priors  
  > "with 90 walkers and 18000 steps after a burn in of 2000 steps" (Fitting and MCMC results)
   - fitting: emcee with uniform priors on log I0, log I1, gamma, sigma0, sigma1, i, PA, dRA, dDec  
  > "We assume uniform priors for the fitted parameters" (Fitting and MCMC results)
   - validation: Residual visibilities imaged, max 3.3 sigma with no coherent pattern  
  > "the residuals are clearly low in flux ($3.3\sigma$ at maximum), and do not show a coherent pattern" (3.3 Continuum intensity profile)
2. **Measure CO flux and radii**: Curve of growth in elliptical apertures from moment maps/images using continuum inclination, PA and center  
  > "The aperture radius is determined via a curve-of-growth method, with successively larger elliptical apertures" (3.2 Radial extent of CO)
   - fitting: _not stated_
   - validation: _not stated_
3. **Estimate continuum optical depth**: Mid-plane temperature profile from stellar luminosity, then invert I = B(T)(1-exp(-tau)) using the best-fit model  
  > "For the intensity profile we used the best fit model." (3.3 Continuum intensity profile)
   - parameter: flaring angle 0.02  
  > "which we set equal to $0.02$" (3.3 Continuum intensity profile)
   - fitting: _not stated_
   - validation: _not stated_
4. **Test for inner cavity**: Add R_trunc to the intensity profile and refit with 100 walkers; upper limit from 95% of MC realizations  
  > "The data do not show signatures of a cavity, with an upper limit on $R_{\rm trunc}$ of $0.54\,$AU" (3.3 Continuum intensity profile)
   - software: GALARIO, emcee
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7: calibration, self-calibration, concat, clean imaging  
  > "The data were calibrated using the `CASA` package, version 4.7" (2 Observations and data reduction)
- **GALARIO** : uv-plane modeling of continuum  
  > "we use the GALARIO code" (3.1 Radial extent of continuum)
- **emcee** : MCMC sampling  
  > "an MCMC sampler with the `emcee` package" (Fitting and MCMC results)
- **matplotlib** : figures  
  > "All the figures were generated with the `python`-based package `matplotlib`" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Integrated continuum flux density | 9.75 | 0.12 | mJy | 1 | The derived integrated flux density is $9.75\pm0.12\,$mJy |
| Dust radius enclosing 68% of flux | 14.0 | 0.3 | AU | 1 | The radius enclosing 68% of the continuum flux density is $14.0\pm0.3\,$AU |
| 12CO J=2-1 integrated flux | 1937 | 54 | mJy km/s | 2 | The integrated flux of the line is $1937\pm54\,$mJy km s$^{-1}$ |
| Gas radius enclosing 68% of 12CO flux | 75 | 5 | AU | 2 | The radius enclosing $68\%$ of the $^{12}$CO $J$=2-1 flux is $75\pm$5 AU. |
| R_gas/R_dust at 68% | 5.4 | not stated | dimensionless | 2 | At the $68\%$ enclosing flux radius the ratio of $R_{\rm gas}$ to $R_{\rm dust}\approx5.4$ |
| R_gas/R_dust at 90% | 3.9 | not stated | dimensionless | 2 | while at the $90\%$ enclosing flux radius the ratio is $\approx3.9$ |
| Peak optical depth | ~0.5 | not stated | dimensionless | 3 | the peak of $\tau$ being $\sim0.5$ |
| Upper limit on cavity radius | 0.54 | not stated | AU | 4 | with an upper limit on $R_{\rm trunc}$ of $0.54\,$AU |
| Disk inclination | 55.1 | ±1.0 | deg | 1 | $55.1^{+1.0}_{-1.0}$ |

## Qualitative findings

- Continuum shows no significant substructure at ~55x32 mas resolution  
  > "The continuum intensity profile does not show any significant level of substructure at the angular resolution of the observations" (3.3 Continuum intensity profile)

## Claim tuples

- H: Is the gas disk much more extended than the mm dust in a compact disk? | E: Compared 68% and 90% enclosed-flux radii of 12CO and continuum | R: R_gas/R_dust ≈ 5.4 (68%) and ≈ 3.9 (90%) versus 1.96 typical in Lupus | F: Large gas-to-dust size ratio argues for efficient radial drift | **supported**
- H: Does the compact disk host rings, gaps or an inner cavity? | E: uv-plane fit with smooth profile, residual imaging, added truncation radius | R: No coherent residuals; R_trunc < 0.54 AU | F: No substructure or cavity detected at this resolution | **supported**
- H: Are faint disks scaled-down versions of large disks? | E: Compared intensity profile with DSHARP disks | R: Profile resembles inner regions of DSHARP disks without outer rings | F: Faint disks are not scaled-down versions | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Functional form chosen from the azimuthally averaged image profile  
  > "By analysing the azimuthally averaged profile obtained from the image, we decided to use the functional form" (3.1 Radial extent of continuum)
- Alternative: Adding rings and gaps to the model gave no better constraint  
  > "Some attempts have been made to refine the model by adding rings and gaps, but no better constraint was obtained." (3.3 Continuum intensity profile)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas surface density cannot be retrieved, so dust-size vs dust-to-gas depletion cannot be disentangled  
  > "Disentangling between the two effects requires knowing the gas surface density, which cannot be retrieved with the present data." (4 Discussion and conclusions)
- Caveat (inferred, ours): Single disk
- Caveat (inferred, ours): CO optical thickness and 12CO-only tracer affect gas radius
- Caveat (inferred, ours): Gas radius uses lower-resolution tapered data
- Caveat (inferred, ours): Continuum size uncertainties are statistical only

## Reproducibility

- Data public (paper): ALMA project 2016.1.00715.S acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00715.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Clean parameters and masks
- Missing: CO aperture details
- Missing: GALARIO version
- Data volume (inferred): ~50-150 GB raw for two long-baseline executions
- Score (inferred): 3/5, Data and main steps are described with an MCMC prior list, but imaging details are missing.
- Rediscovery candidate: yes, Archive data are likely public after proprietary period, recipe is largely complete, and results are numeric (radii, flux).

## Links

- Method: (cite: 2018MNRAS.476.4527T) (GALARIO uv modeling code)
- Method: (cite: 2018ApJ...859...21A) (CO curve-of-growth and radius method)
- Companion: (cite: 2018ApJ...869L..41A) (DSHARP comparison sample)
- Companion: (cite: 2019arXiv190306190T) (Models of gas/dust size ratio)
- Related: DSHARP
- Related: Lupus ALMA survey

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 43,
  "rate": 0.623
 },
 "evidence_ok": true
}
```
