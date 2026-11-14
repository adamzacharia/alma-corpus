# Resolved Millimeter-wavelength Observations of Debris Disks around Solar-type Stars

`2016ApJ...816...27S` | The Astrophysical Journal 2016 | first author: Steele, Amy | arXiv: 1510.08890 | DOI: 10.3847/0004-637X/816/1/27

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: What are the radii, widths, grain properties and axisymmetry of the cold outer debris belts around five solar-type FEPS stars, derived with a uniform analysis of millimeter interferometry plus SED?  
  > "We simultaneously model the broad-band photometric data and resolved millimeter visibilities to constrain the dust temperatures and disk morphologies, and perform an MCMC analysis to fit for basic structural parameters." (abstract)
- Target **HD 377**: coordinates 00:08:26 +06:37:01 (J2000)  
  > "| HD 377 | 40 | 32 | 00:08:26 | +06:37:01 | G2 V | 5852 | 0.09 |" (Table 1); z/distance 40 pc  
  > "| HD 377 | 40 | 32 | 00:08:26 | +06:37:01 | G2 V | 5852 | 0.09 |" (Table 1); distance from _not stated_
- Target **HD 8907**: coordinates 01:28:34 +42:16:04 (J2000)  
  > "| HD 8907 | 34 | 320 | 01:28:34 | +42:16:04 | F8 | 6250 | 0.32 |" (Table 1); z/distance 34 pc  
  > "| HD 8907 | 34 | 320 | 01:28:34 | +42:16:04 | F8 | 6250 | 0.32 |" (Table 1); distance from _not stated_
- Target **HD 61005**: coordinates 07:35:47 -32:12:14 (J2000)  
  > "| HD 61005 | 35 | 100 | 07:35:47 | $-3$2:12:14 | G3/5 V | 5456 | $-0.25$ |" (Table 1); z/distance 35 pc  
  > "| HD 61005 | 35 | 100 | 07:35:47 | $-3$2:12:14 | G3/5 V | 5456 | $-0.25$ |" (Table 1); distance from _not stated_
- Target **HD 104860**: coordinates 12:04:34 +66:20:12 (J2000)  
  > "| HD 104860 | 48 | 32 | 12:04:34 | +66:20:12 | F8 | 5950 | 0.12 |" (Table 1); z/distance 48 pc  
  > "| HD 104860 | 48 | 32 | 12:04:34 | +66:20:12 | F8 | 5950 | 0.12 |" (Table 1); distance from _not stated_
- Target **HD 107146**: coordinates 12:19:06 +16:32:54 (J2000)  
  > "| HD 107146 | 29 | 100 | 12:19:06 | +16:32:54 | G2 V | 5859 | 0.04 |" (Table 1); z/distance 29 pc  
  > "| HD 107146 | 29 | 100 | 12:19:06 | +16:32:54 | G2 V | 5859 | 0.04 |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00470.S
- bands: 230 GHz (1.3 mm) and/or 345 GHz (0.87 mm)  
  > "The disks were observed at 230 GHz (1.3 mm), and/or 345 GHz (0.87 mm)." (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: full 8 GHz (SMA and CARMA)  
  > "For all observations, the correlator was configured to provide maximum sensitivity across the full 8 GHz available bandwidth." (2 Observations)
- arrays: SMA, CARMA (15 antennas), ALMA Cycle 0 (HD 107146 only)  
  > "Each of the disks in this sample was observed with the Submillimeter Array (SMA)." (2 Observations); "The 1.3 mm wavelength ALMA continuum data on HD 107146 originate from Cycle 0 observations by (cite: Ricci15)." (2 Observations)
- configurations: SMA Subcompact, Compact, Extended  
  > "Our observations utilized the Subcompact, Compact, and Extended configurations of the SMA to sample baselines between 9 and 226 m" (2 Observations)
- baselines: _not stated_
- angular resolution: as fine as 2.2" at 230 GHz and 0.6" at 345 GHz (SMA); ~2" overall  
  > "to achieve an angular resolution as fine as 2.2” at 230 GHz and 0.6” at 345 GHz" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: SMA 2008-2012; ALMA 2012 Jan to 2013 Jan; CARMA Apr-Jun 2012  
  > "The sources were observed for two to four nights between 2008 and 2012." (2 Observations)
- pi or archival as stated: _not stated_
- Other facility **Spitzer FEPS**: Photometry and Kurucz photosphere models for SEDs  
  > "drawn from the FEPS Legacy Survey archive" (3.1 SED and Visibility Modeling)
- External data: Broadband photometry used for SED fitting (table of fluxes 1.24 um to 1.3 mm)  
  > "one comparing the model disk SED to photometric data from the literature" (3.2 Error Analysis) [from Table of photometry with references a-h (not resolved in text)]
- External data: PA and inclination of HD 104860 from Morales13  
  > "For HD 104860, the PA and $i$ were taken from (cite: Morales13)" (3.1 SED and Visibility Modeling) [from (cite: Morales13)]
- External data: PA and inclination of HD 61005 and HD 107146 from scattered light  
  > "were adopted from scattered light observations of the disks (see (cite: Buenzli10) and (cite: Ardila04))" (3.1 SED and Visibility Modeling) [from (cite: Buenzli10); (cite: Ardila04)]
- External data: Astrosilicate opacities and density  
  > "We assume that the grains are astronomical silicates (astrosilicates) with a bulk density of $2.7\, \text{g}\,\text{cm}^{-3}$ (cite: DraineLee84)." (3.1 SED and Visibility Modeling) [from (cite: DraineLee84); (cite: Draine06)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Solar system bodies (Uranus, Neptune, Titan, Callisto, Ceres) for SMA; Mars and MWC349 for CARMA; Mars/Titan for ALMA  
  > "Solar system bodies with well-determined flux models were used to calibrate the absolute flux scale of the observations." (2 Observations); "Mars and MWC349 were used to calibrate the flux" (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: naturally weighted maps quoted for RMS noise  
  > "the RMS noise in the naturally weighted map" (2 Observations)
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

- ALMA HD 107146 data collection and reduction  
  > "The data collection and reduction processes are fully described in their paper." (2 Observations) [from (cite: Ricci15)]
- Modeling approach for SED and visibilities  
  > "The general modeling approach closely follows that described in (cite: Ricarte13)." (3 Analysis and Results) [from (cite: Ricarte13)]
- SMA data of HD 107146 and HD 61005 previously published  
  > "more detail about those data are available in their respective publications." (2 Observations) [from (cite: Hughes11); (cite: Ricarte13)]
- Grain emission efficiency Q(lambda) parameterization  
  > "we approximate the grain emission efficiency following (cite: Williams04)" (3.1 SED and Visibility Modeling) [from (cite: Williams04)]

### Not stated but needed to reproduce (our reading)

- Imaging weighting/robust, cell size and cleaning parameters for the displayed images
- Calibration software and versions for SMA, CARMA and ALMA
- Lower/upper bounds of uniform priors
- Treatment of the HD 107146 ALMA visibility averaging/time binning
- Exact burn-in length and convergence criterion
- Stellar masses used for blowout sizes
- Source of distances

## Analysis recipe

1. **Fit disk centroids and initial fluxes**: Elliptical Gaussian (elliptical ring for HD 107146) fit to continuum visibilities  
  > "We calculated the centroid of the disk using an elliptical Gaussian (or, for HD 107146, an elliptical ring) fit to the continuum visibilities with the MIRIAD task `uvfit`." (3.1 SED and Visibility Modeling)
   - software: MIRIAD
   - fitting: _not stated_
   - validation: Offsets consistent with stellar position given proper motion  
  > "All of the offset positions were consistent with the expected position of the star to within the uncertainties, taking into account the measured proper motion." (3.1 SED and Visibility Modeling)
2. **Set disk geometry (PA, inclination)**: Literature values for HD 61005, HD 107146, HD 104860; grid search maximizing visibility amplitudes for HD 377 and HD 8907  
  > "a grid search fit of PA and $i$ was used to maximize the visibility amplitudes" (3.1 SED and Visibility Modeling)
   - fitting: _not stated_
   - validation: Results consistent with uvfit  
  > "the results were consistent with the `uvfit` results" (3.1 SED and Visibility Modeling)
3. **Build SED + visibility disk model**: Kurucz-Lejeune photosphere + cold resolved disk + warm 100 K belt; modified blackbody with Q=1-exp(-(lambda0/lambda)^beta); model image sampled at data uv with uvmodel  
  > "We then sample the model image at the same spatial frequencies as the data, using the MIRIAD command `uvmodel`." (3.1 SED and Visibility Modeling)
   - software: MIRIAD
   - parameter: p fixed to 0 except HD 107146; warm belt temperature fixed at 100 K; pixel size 1% of spatial scale of longest baseline  
  > "we fix the temperature at 100 K and vary only the mass" (3.1 SED and Visibility Modeling); "The pixel size is set to be 1% of the spatial scale sampled by the longest baseline." (3.1 SED and Visibility Modeling)
   - assumption: Astrosilicate grains, density 2.7 g cm^-3, optically thin, radiative equilibrium  
  > "We calculate the temperature of the grains by assuming that they are in radiative equilibrium with the central star and that the disk is optically thin." (3.1 SED and Visibility Modeling)
   - fitting: _not stated_
   - validation: AIC used for warm belt significance  
  > "We used the Akaike information criterion (AIC) to place a $3\sigma$ upper limit on the warm belt mass of HD 8907" (3.1 SED and Visibility Modeling)
4. **MCMC fit of six parameters**: Affine-invariant stretch-move MCMC on total chi2 = chi2_SED + chi2_VIS  
  > "We add the chi-squared values for the SED and visibilities and use the total $\chi^2$ as the statistic for goodness-of-fit" (3.2 Error Analysis)
   - software: emcee-like custom sampler
   - parameter: 50 walkers, 5000 trials, burn-in a few hundred trials discarded  
  > "We run 50 walkers through 5000 trials and discard trials for which the $\chi^2$ values have not yet converged" (3.2 Error Analysis)
   - fitting: Uniform priors; a, M_D, M_B initialized in log space; R_in, beta (and p) linear  
  > "We assume uniform priors for all variables." (3.2 Error Analysis)
   - validation: Best fit = lowest chi2 walker; 1 sigma from 68% of PDF; residual images in visibility domain  
  > "The global best fit model is chosen from the MCMC walker position with the lowest $\chi^2$ value across the entire set of walkers and trials." (4 Results)
5. **Derive grain size distribution slope and compare radii/blowout**: q ≈ beta/beta_s + 3 with beta_s≈1.8; blowout size from radiation pressure formula; R_in/R_BB comparison  
  > "Solving for $q$, we find that $q \approx (\beta/\beta_s) + 3$." (5.1 Grain Sizes)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MIRIAD** : uvfit centroid fits and uvmodel model sampling  
  > "fit to the continuum visibilities with the MIRIAD[^2] task `uvfit`" (3.1 SED and Visibility Modeling)
- **emcee** : Similar affine-invariant sampler implemented (stretch moves only)  
  > "We implement a sampler that utilizes only stretch moves, similar to the affine-invariant MCMC sampler, `emcee`, written in Python" (3.2 Error Analysis)
- **Astropy** : acknowledged use  
  > "The research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HD 377 R_in | 30.1 | +8.4/-6.3 | AU | 4 | $30.1^{+8.4}_{-6.3}$ |
| HD 107146 R_in | 30.8 | +2.0/-1.7 | AU | 4 | $30.8^{+2.0}_{-1.7}$ |
| HD 107146 width Delta R | 129 | +2.1/-1.9 | AU | 4 | $129^{+2.1}_{-1.9}$ |
| HD 107146 beta | 0.75 | +0.02/-0.05 | dimensionless | 4 | $0.75^{+0.02}_{-0.05}$ |
| Typical grain size slope q | 3.5 | 0.5 | dimensionless | 5 | We therefore derive a typical $q$ value of $3.5\pm 0.5$. |
| Median inner radius | 42 | typical ±10 | AU | 4 | The median value was 42 AU, and all but one of the disks (HD 61005) was consistent with that median value to within the uncertainties. |

## Qualitative findings

- All disks consistent with axisymmetric dust distributions within uncertainties; only a single 3-sigma residual peak in HD 107146  
  > "There is a localized 3-sigma peak in the ALMA HD 107146 residual map" (5.3 Deviations from an Axisymmetric Model)

## Claim tuples

- H: Are the outer belts of solar-type stars scaled-up Kuiper Belts? | E: Joint SED + visibility MCMC fit of five disks | R: R_in 28-69 AU; widths mostly unresolved | F: Disks consistent with scaled-up Kuiper belts | **supported**
- H: Do mm grains have sizes near blowout? | E: Compared fitted characteristic grain sizes to blowout size | R: Blowout ~0.3 um, characteristic size ~1-30 um | F: Grain sizes comparable to blowout size, consistent with collisional cascade (q~3.5) | **supported**
- H: Do the disks show non-axisymmetric structure? | E: Residual visibility imaging | R: No significant residuals | F: No asymmetries detected within limited S/N | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Simplified modified blackbody approach is computationally efficient enabling a full MCMC  
  > "thereby allowing us to perform a robust statistical analysis of the data using an affine-invariant MCMC sampler" (3 Analysis and Results)
- Alternative: One vs two-component disk for HD 104860; two-component preferred  
  > "We analyzed the SED and visibilities with one component as well as two, and find that a two-component disk best reproduces the thermal SED" (5.2 Inner Radii and Disk Widths)
- How they decided it was enough: _not stated_
- Limitation (authors): Code is not entirely internally self-consistent; geometry of HD 377/8907 highly uncertain  
  > "so the code is not entirely internally self-consistent" (3.1 SED and Visibility Modeling); "These geometric parameters are highly uncertain" (3.1 SED and Visibility Modeling)
- Caveat (inferred, ours): Disk widths mostly unresolved so p fixed to 0
- Caveat (inferred, ours): Mixed use of AIC and BIC
- Caveat (inferred, ours): Marginally resolved HD 377 and HD 8907 make geometry priors weak
- Caveat (inferred, ours): Only one ALMA dataset, others lower-S/N

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Custom MCMC/SED code not released
- Missing: SMA and CARMA reduction details
- Missing: Prior ranges
- Missing: Photometry reference key
- Data volume (inferred): ~10-50 GB (ALMA Cycle 0 plus SMA/CARMA)
- Score (inferred): 3/5, Recipe is described but custom code, priors and reduction details are missing; only ALMA data demonstrably public.
- Rediscovery candidate: no, Custom modeling code unavailable and ALMA is only one of several datasets.

## Links

- Method: (cite: Ricarte13) (Modeling approach followed)
- Method: (cite: Ricci15) (ALMA HD 107146 data reduction)
- Companion: (cite: Hughes11) (Earlier SMA HD 107146 data)
- Related: FEPS Spitzer Legacy

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 48,
  "rate": 0.539
 },
 "evidence_ok": true
}
```
