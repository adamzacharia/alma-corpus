# The Disk Substructures at High Angular Resolution Program (DSHARP). VIII. The Rich Ringed Substructures in the AS 209 Disk

`2018ApJ...869L..48G` | The Astrophysical Journal Letters 2018 | first author: Guzmán, Viviana V. | arXiv: 1812.04046 | DOI: 10.3847/2041-8213/aaedae

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What is the ring/gap substructure of the AS 209 disk in 1.25 mm dust continuum and 12CO 2-1 emission at 5 au resolution, and what could cause it?  
  > "We model the visibilities with a parametric representation of the radial surface brightness profile, consisting of a central core and 7 concentric Gaussian rings." (abstract)
- Target **AS 209**: coordinates _not stated_; z/distance 121±2 pc  
  > "The star is located to the northeast of the main Ophiuchus star-forming region, at a distance of $121\pm2$ pc (cite: Gaia2018)." (1 Introduction); distance from Gaia (Gaia2018)  
  > "The star is located to the northeast of the main Ophiuchus star-forming region, at a distance of $121\pm2$ pc (cite: Gaia2018)." (1 Introduction)

## Data provenance

- ALMA projects: 2016.1.00484.L, 2015.1.00486.S
- bands: Band 6  
  > "The AS 209 disk was observed with ALMA in Band 6 in September 2017 in configurations C40-8/9." (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-8/9 (Sept 2017), C40-5 (May 2017), plus archival data  
  > "Shorter-baselines were observed in May 2017 in configuration C40-5." (2 Observations)
- baselines: _not stated_
- angular resolution: continuum beam 38 mas x 36 mas; CO beam 95 mas x 70 mas  
  > "The resulting continuum image has a beam of 38 mas $\times$ 36 mas, PA of $68^{\circ}$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 19 uJy/beam; CO rms 0.8 mJy/beam per channel  
  > "a rms noise of 0.8 mJy beam$^{-1}$ per channel." (2 Observations)
- time on source: _not stated_
- observing dates: May 2017 and September 2017  
  > "observed with ALMA in Band 6 in September 2017" (2 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- External data: Midplane temperature profile used to estimate snowline locations  
  > "using the midplane temperature derived by (cite: Andrews2009)" (4.1) [from (cite: Andrews2009)]
- External data: Hydrodynamical simulation of AS 209 (planet at 99 au, 0.087 MJ)  
  > "The planet responsible for the gaps has a mass of 0.087 M$_J$." (4.1) [from (cite: Zhang2018)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Short baselines self-calibrated first, then combined short+long baselines; solutions applied to CO  
  > "we first self-calibrated the short baselines, and in a second step self-calibrated the combined observations of short- and long-baselines." (2 Observations)

### Imaging

- task: CASA 5.1 clean, multi-scale  
  > "The continuum observations were cleaned in `CASA` 5.1, using the multi-scale option and a robust parameter of $-0.5$." (2 Observations)
- deconvolver: _not stated_
- weighting robust: continuum robust = -0.5; CO robust = 1.0  
  > "then cleaned with a robust parameter of 1.0." (2 Observations)
- uv taper: FWHM 37 mas x 10 mas, PA 162 deg  
  > "A taper with FWHM of 37 mas $\times$ 10 mas and position angle (PA) of 162$^{\circ}$ was used" (2 Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian mask for CO  
  > "A Keplerian mask was used to help the cleaning process." (2 Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CO regridded to 0.35 km/s channels  
  > "first regridded to channels of 0.35 km s$^{-1}$" (2 Observations)
- final beam: continuum 38x36 mas PA 68; CO 95x70 mas PA 97  
  > "The resulting $^{12}$CO image has a beam of 95 mas $\times$ 70 mas, PA of $97^{\circ}$" (2 Observations)
- final rms: 19 uJy/beam continuum; 0.8 mJy/beam/channel CO  
  > "a rms noise of 19 $\mu$Jy beam$^{-1}$." (2 Observations)

### Inherited from earlier work

- Detailed observation description and data reduction  
  > "A detailed description of the observations and data reduction process can be found in (cite: Andrews2018)." (2 Observations) [from (cite: Andrews2018)]

### Not stated but needed to reproduce (our reading)

- Image size and cell size
- Multiscale scales and clean threshold/niter
- Self-calibration solution intervals
- Line-free channels and continuum subtraction for CO
- Flux calibrator and flux scale uncertainty
- MCMC walkers, steps, priors, burn-in
- Weighting/relative weights when combining the three projects' data
- Lines/spectral windows used for continuum

## Analysis recipe

1. **Image continuum and CO**: CASA clean with multiscale, taper (continuum), Keplerian mask (CO)  
  > "The continuum observations were cleaned in `CASA` 5.1, using the multi-scale option and a robust parameter of $-0.5$." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit radial profile of rings in uv-plane**: Sum of concentric Gaussian rings, Hankel transform to visibilities, fit to deprojected radially averaged binned visibilities  
  > "To speed up the fitting method, the observed visibilities are first deprojected, radially averaged and binned." (3.1.1)
   - software: emcee
   - parameter: uv-points 10 to 10000 kλ in 10 kλ steps; 27 free parameters (23 ring, 4 geometry)  
  > "We include *uv*-points from 10 to 10000 k$\lambda$, in steps of 10 k$\lambda$." (3.1.1)
   - assumption: Axisymmetric emission; number of rings chosen by visual inspection  
  > "The number of rings is chosen through visual inspection of the cleaned emission map and the deprojected radial profile" (3.1.1)
   - fitting: Affine-invariant MCMC (emcee); best fit = 50th percentile, errors 16th/84th percentiles  
  > "The uncertainties are calculated from the 16th and 84th percentiles." (3.1.1)
   - validation: Cleaned image of model and of residual visibilities compared with data; residuals remain near center  
  > "However, some residuals remain near the disk center." (3.1.1)
3. **CO moment map and radial profile**: Moment-zero integrated -3 to 14 km/s, clip S/N<3, azimuthally averaged deprojected profile of East side  
  > "Pixels with S/N ratio lower than 3 have been clipped to highlight the substructure of the emission." (3.2)
   - fitting: _not stated_
   - validation: Gaps also seen in individual channel maps  
  > "as the gaps are also seen with even more clarity in the individual channels" (3.2)

## Software

- **CASA** 5.1: cleaning continuum and CO  
  > "cleaned in `CASA` 5.1" (2 Observations)
- **emcee** : MCMC fit of ring model  
  > "We use the affine invariant MCMC sampler implemented in the `emcee` package" (3.1.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk inclination | 34.883 | +0.0151/-0.0042 | deg | 2 | $34.883_{-0.0042}^{+0.0151}$ |
| Position angle | 85.764 | +0.0184/-0.0061 | deg | 2 | $85.764_{-0.0061}^{+0.0184}$ |
| Ring B74 radius | 74.08 | +0.02/-0.01 | au | 2 | $74.08_{-0.01}^{+0.02}$ |
| Ring B120 radius | 120.42 | ±0.02 | au | 2 | $120.42_{-0.02}^{+0.02}$ |
| Ring B15 radius | 15.13 | +0.02/-0.03 | au | 2 | $15.13_{-0.03}^{+0.02}$ |
| Total flux density | 0.27 | not stated | Jy | 2 | $F_{tot} \equiv V(\rho=0) = 0.27$ Jy. |
| CO gap radii | 45, 75, 120, 210 | not stated | au | 3 | presents 4 main gaps or emission decrements in the outer disk, near 45, 75, 120 and 210 au. |

## Qualitative findings

- Outermost CO gap at ~210 au lies beyond the mm dust edge, so it is not due to dust opacity  
  > "Therefore, it cannot be explained by dust opacity and must be a real decrease in the $^{12}$CO column density at this radius." (3.2)

## Claim tuples

- H: Can the AS 209 dust continuum be described by concentric Gaussian rings? | E: uv-plane MCMC fit of a core plus 7 Gaussian rings | R: Rings at 15, 27, 41, 74, 92, 120, 139 au with low residuals | F: Emission is well represented by narrow concentric rings, with some residual in the inner disk | **supported**
- H: Is the outer CO gap caused by dust opacity? | E: Compare CO gaps with dust ring radii | R: Gap at 210 au is beyond the dust edge | F: Requires a real CO column density reduction (chemistry or gas depletion) | **supported**
- H: Are the gaps due to snowlines or planets? | E: Compare with snowline temperatures and hydrodynamical simulations | R: Snowlines unlikely to explain all gaps; low-mass planet simulations reproduce rings | F: Planets favoured but not confirmed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Snowline-induced gaps, zonal flows, dead zones judged unlikely or problematic  
  > "it is hard to explain how condensation fronts alone could produce such wide gaps." (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): West side of the disk affected by cloud contamination  
  > "The West side of the disk is moderately affected by cloud contamination" (3.2)
- Caveat (inferred, ours): Ring count chosen by eye; no model comparison
- Caveat (inferred, ours): Faint broad rings are poorly described by Gaussians
- Caveat (inferred, ours): Continuum subtraction may bias CO gaps
- Caveat (inferred, ours): Position-angle/inclination errors look underestimated (formal)

## Reproducibility

- Data public (paper): Data come from ALMA projects, archival ones cited  
  > "We use additional archival data from projects 2013.1.00226" (2 Observations)
- Products in archive: _not stated_
- Missing: MCMC settings and priors
- Missing: Imaging grid parameters
- Missing: Self-cal details (in Andrews2018)
- Missing: CO continuum subtraction channels
- Data volume (inferred): several hundred GB raw across three projects
- Score (inferred): 3/5, Public data and a clear parametric model, but imaging and MCMC details are deferred to another paper or missing.
- Rediscovery candidate: yes, Public data, a well-defined ring model with numeric table of best-fit parameters.

## Links

- Method: (cite: Andrews2018) (DSHARP data reduction and self-calibration)
- Method: (cite: Foreman-Mackey2013) (emcee sampler)
- Companion: (cite: Huang2018a) (DSHARP ring analysis, ring naming)
- Companion: (cite: Zhang2018) (hydrodynamical simulation of AS 209)
- Related: DSHARP

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00226.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 33,
  "rate": 0.532
 },
 "evidence_ok": true
}
```
