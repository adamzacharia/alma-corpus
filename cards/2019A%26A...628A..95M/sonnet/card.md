# Observational constraints on dust disk sizes in tidally truncated protoplanetary disks in multiple systems in the Taurus region

`2019A&A...628A..95M` | Astronomy and Astrophysics 2019 | first author: Manara, C. F. | arXiv: 1907.03846 | DOI: 10.1051/0004-6361/201935964

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Do dust disks in multiple stellar systems in Taurus have smaller sizes and sharper outer edges than disks around single stars, and are the dust radius to separation ratios consistent with tidal truncation predictions?  
  > "The dust radii of disks around multiple stellar systems are smaller than those around single stars in the same stellar mass range and in the same region." (abstract)
- Target **Ten multiple systems in Taurus (T Tau, UY Aur, RW Aur, DK Tau, HK Tau, CIDA 9, DH Tau, V710 Tau, HN Tau, UZ Tau)**: coordinates per-component RA/Dec in the fit table (e.g. T Tau N 04:21:59.4 +19:32:06.18)  
  > "Distances are obtained by inverting the Gaia parallax when the uncertainty on the parallax is less than 10% of the measured parallax." (Table 1 notes); z/distance 131 pc to 171 pc  
  > "Distances are obtained by inverting the Gaia parallax when the uncertainty on the parallax is less than 10% of the measured parallax." (Table 1 notes); distance from Gaia DR2 parallaxes  
  > "Distances are obtained by inverting the Gaia parallax when the uncertainty on the parallax is less than 10% of the measured parallax." (Table 1 notes)

## Data provenance

- ALMA projects: 2016.1.00164.S
- bands: Band 6 (1.3 mm)  
  > "Our sample was observed with ALMA in Band 6 in 2017 August–September." (2.2 Observations and data reduction)
- frequencies and spectral setup: continuum spw centered at 218 and 233 GHz, 1.875 GHz each, mean 225.5 GHz  
  > "The continuum spectral windows were centered at 218 and 233 GHz, each with a bandwidth of 1.875 GHz, for an averaged frequency of 225.5 GHz" (2.2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.12 arcsec typical beam (~15-20 au)  
  > "These images have a typical beam size of 0.12$^{\prime\prime}$ and continuum rms of 50 $\mu$Jy beam$^{-1}$." (2.2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 50 uJy/beam  
  > "These images have a typical beam size of 0.12$^{\prime\prime}$ and continuum rms of 50 $\mu$Jy beam$^{-1}$." (2.2 Observations and data reduction)
- time on source: ~8-10 min per target  
  > "Each target was observed for $\sim 8-10$ min." (2.2 Observations and data reduction)
- observing dates: 2017 August-September  
  > "Our sample was observed with ALMA in Band 6 in 2017 August–September." (2.2 Observations and data reduction)
- pi or archival as stated: Program PI Herczeg (authors' own snapshot survey)  
  > "The survey of disk structures in Taurus (program 2016.1.00164.S, PI Herczeg)" (2 Sample and observations)
- Other facility **Gaia DR2**: parallaxes/distances to components  
  > "The stellar luminosities are then rescaled to the distance obtained from the parallaxes measured by the Gaia satellite" (2.1 Sample)
- External data: Spectral types and luminosities of targets  
  > "We use the spectral type and the luminosity of the target, when available, derived by (cite: HH14)." (2.1 Sample) [from (cite: HH14)]
- External data: Dynamical masses for T Tau Sa/Sb, UZ Tau E, HN Tau A  
  > "The dynamical mass estimate is also assumed for UZ Tau E (cite: simon00) and HN Tau A (cite: simon17)" (2.1 Sample) [from (cite: schaefer14; kohler16; simon00; simon17)]
- External data: Dust radii and profile fits of 12 smooth single-star disks used as comparison sample  
  > "In a companion paper, (cite: long19) have used our same analysis strategy to determine the intensity profile of the dust emission in the 12 smooth single disks" (4 Results) [from (cite: long19)]
- External data: Gas-to-dust radius ratio of 2 from Lupus disks  
  > "The latter factor was chosen based on the median value obtained through the observation of disks in the Lupus star-forming region with ALMA (cite: ansdell18)." (5.2) [from (cite: ansdell18)]
- External data: Numerical tidal truncation results fitted for b, c parameters  
  > "Now we calculate *b* and *c* by fitting the numerical results from (cite: AL94)" (10.1) [from (cite: AL94)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: phase and amplitude self-calibration applied after standard calibration  
  > "phase and amplitude self-calibrations were applied to our targets to maximize the image signal-to-noise ratio after the standard calibration procedure." (2.2 Observations and data reduction)

### Imaging

- task: CASA tclean  
  > "The continuum images were then created with the CASA task *tclean*, using Briggs weighting with a robust parameter of 0.5." (2.2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "using Briggs weighting with a robust parameter of 0.5" (2.2 Observations and data reduction)
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
- final beam: ~0.12 arcsec  
  > "These images have a typical beam size of 0.12$^{\prime\prime}$" (2.2 Observations and data reduction)
- final rms: 50 uJy/beam  
  > "continuum rms of 50 $\mu$Jy beam$^{-1}$" (2.2 Observations and data reduction)

### Inherited from earlier work

- Data reduction and calibration details, observing conditions and calibrators  
  > "The observing conditions and calibrators for individual targets can be found in Table 2 of (cite: long19), where the details of the data reduction and calibration are described." (2.2 Observations and data reduction) [from (cite: long19)]
- Stellar properties derived as in earlier work  
  > "The stellar properties are obtained as in (cite: long19)." (2.1 Sample) [from (cite: long19)]
- Disk radius definitions (95% and 68% flux radii)  
  > "Following (cite: tazzari17), (cite: tripathi17), and (cite: trapman19) among others, we defined the disk radius" (3 Analysis) [from (cite: tazzari17; tripathi17; trapman19)]
- Gaussian ring profiles for CIDA 9A and UZ Tau E  
  > "Following (cite: long18), we used a single Gaussian ring profile for CIDA 9A" (3 Analysis) [from (cite: long18)]
- Stellar mass from evolutionary tracks as in Pascucci  
  > "as in (cite: pascucci16)" (2.1 Sample) [from (cite: pascucci16)]

### Not stated but needed to reproduce (our reading)

- Priors and parameter bounds for the MCMC fits
- Initial walker positions and exact convergence criterion
- Visibility weights rescaling procedure details (factor sqrt(3.5) applied)
- Exact calibrators, self-calibration solution intervals and CASA version (deferred to Long et al. 2019)
- Number of uv-averaged channels and any uv-range cut
- Reynolds numbers adopted (three values not listed in main text)
- Whether the 1.33 mm flux in radii uses the fitted profile extrapolated to infinity
- Cell size, image size, and masks

## Analysis recipe

1. **Derive stellar properties and distances**: Gaia DR2 parallaxes for distances; spectral type to Teff, with luminosity, to masses via evolutionary tracks  
  > "combine this with the distance corrected stellar luminosity to infer the stellar masses using the evolutionary models by (cite: baraffe15) and the nonmagnetic models by (cite: feiden16)" (2.1 Sample)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit continuum visibilities of each disk**: Sum of axisymmetric model visibilities per component, power law with exponential cutoff (Gaussian rings for CIDA 9A, UZ Tau E); visibilities averaged per spw to one channel  
  > "To fit the continuum visibilities of a multiple system made of $M$ components, we computed the total model visibilities as the sum of the visibilities of the individual components" (3 Analysis)
   - software: Galario, emcee
   - parameter: 150 walkers, ~20000 steps (1 disk); 200 walkers, >25000 steps (2 disks); 400 walkers, 31000 steps (UZ Tau)  
  > "typically we used 150 walkers and $\sim$20000 steps for the cases where only one disk is detected (8 parameters), 200 walkers and more than 25000 steps for the cases where two disks are detected (16 parameters)" (3 Analysis)
   - assumption: axisymmetric brightness profile, independent geometry per disk  
  > "each disk is modeled with an independent brightness profile and geometry" (3 Analysis)
   - fitting: emcee ensemble MCMC with Gaussian likelihood; medians of posterior, 16th-84th percentile uncertainties; last 3000-10000 steps used  
  > "We explored the parameter space using the Markov chain Monte Carlo (MCMC) ensemble sampler `emcee` (cite: emcee) and we adopted a Gaussian likelihood" (3 Analysis)
   - validation: Reduced chi2 ~3.5 (6.4 for T Tau), attributed to CASA weights underestimated; uncertainties corrected; R_eff compared with Gaussian and Nuker profile fits  
  > "We verified that the values of $R_{\rm eff,dust}$ obtained with this functional form are compatible with those obtained using a Gaussian function" (3 Analysis)
3. **Compute dust radii and flux**: R_disk,dust enclosing 95% and R_eff,dust enclosing 68% of flux; uncertainties from 1000 chains  
  > "The uncertainties on these values are obtained by calculating the radii and the flux with the values obtained with 1000 different chains" (3 Analysis)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare multiples with single smooth disks**: Two-sided K-S tests on radii, gamma1 and gamma2 distributions vs. singles from Long et al. 2019  
  > "We perform also the Kolmogorov–Smirnov (K-S) two-sided test for the null hypothesis that the samples of dust radii around single stars and around primary stars in multiple systems are drawn from the same continuous distribution." (4.1)
   - fitting: _not stated_
   - validation: Repeated excluding CIDA 9A and UZ Tau E  
  > "This same result is found when excluding the two disks around primary stars showing substructures (CIDA 9A and UZ Tau E)" (4.1)
5. **Relative disk inclinations**: Spherical law of cosines with fitted inclinations and position angles  
  > "We computed the relative inclination of the disks in each system using the spherical law of cosines" (4.3)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compare radii/separation with tidal truncation**: Analytic truncation radius from Artymowicz & Lubow fit (Roche lobe times b e^c + 0.88 mu^0.01); derive minimum eccentricity for i=0 or coplanar orbit, with truncation radius = dust radius or 2x dust radius  
  > "We thus explore here the eccentricities that would be derived using the measured dust disk radii as a value for the truncation radius" (5.2)
   - parameter: three Reynolds numbers; gas radius = 2 x dust radius  
  > "using an estimate of the gas disk radii that is two times larger than the dust radii" (5.2)
   - assumption: Coplanar disks and orbit for the theoretical truncation radius; apoastron gives minimum eccentricity  
  > "This is a lower limit to the real eccentricity of the orbit" (5.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : tclean continuum imaging (Briggs, robust 0.5)  
  > "The continuum images were then created with the CASA task *tclean*" (2.2 Observations and data reduction)
- **Galario** : computing model visibilities  
  > "We used `Galario` (cite: tazzari18) to compute the model visibilities" (3 Analysis)
- **emcee** : MCMC sampling of model parameters  
  > "Markov chain Monte Carlo (MCMC) ensemble sampler `emcee` (cite: emcee)" (3 Analysis)
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median R_disk,dust of disks in multiple systems (primaries / secondaries) | 21 / 15 | not stated | au | 4 | the median value of the dust radii distribution ($R_{\rm disk,dust}$=21 au and $R_{\rm disk,dust}$=15 au, respectively) |
| Median R_disk,dust of smooth single disks | 34 | not stated | au | 4 | is smaller in multiple systems than in single systems ($R_{\rm disk,dust}$=34 au) |
| K-S p-value radii singles vs primaries | <1e-5 | not stated | dimensionless | 4 | The results exclude this hypothesis with p-values$<10^{-5}$ |
| K-S p-value gamma2 singles vs multiples | <1e-5 | not stated | dimensionless | 4 | with p-values$<10^{-5}$ when performing a K-S test of the two distributions |
| UZ Tau E R_disk,dust | 86.3 | +0.26/-0.42 | au | 3 | / UZ Tau E   / 04:32:43.1 / +25:52:30.63 / 0.4424$_{-0.0022}^{+0.0011}$ / 57.9$_{-0.29}^{+0.14}$ / 0.6588$_{-0.0032}^{+0.0020}$ / 86.3$_{-0.42}^{+0.26}$ |
| Fraction of disk pairs requiring e>0.5 (i=0, dust radius as truncation) | 9 of 11 | not stated | dimensionless | 6 | quite high ($e>0.5$ in 9/11 cases) assuming the truncation radius to be equal to the dust disk radius |

## Qualitative findings

- Disks around secondaries are statistically smaller than primaries and singles; outliers T Tau S and HK Tau B  
  > "Two main outliers are however present: T Tau S and HK Tau B." (4.1)
- No clear correlation of disk flux with projected separation in this sample  
  > "We do not find a clear correlation between the two components" (4.4)

## Claim tuples

- H: Disks in multiple systems are smaller than disks around single stars | E: Visibility fits of 1.3 mm continuum and K-S comparison with smooth single disks | R: Median R_disk,dust 21 au (primaries) vs 34 au (singles); p<1e-5 | F: Dust disks in multiples are smaller | **supported**
- H: Disk outer edges in multiples are sharper | E: Compare gamma2 exponent distributions | R: gamma2 larger in multiples, p<1e-5 | F: Steeper outer edge, plausibly tidal truncation | **supported**
- H: Measured dust radii are consistent with tidal truncation predictions | E: Compare R/a_p with analytic truncation models and derive minimum eccentricities | R: e>0.5 in 9/11 cases if dust radius is truncation radius; reasonable if gas radius is 2x dust | F: Consistent only with high eccentricities or gas radii twice dust radii | **partially**
- H: Disks in a multiple system are coplanar | E: Relative inclinations from fitted inclination and PA | R: Only UZ Tau and UY Aur near 0 deg, others large | F: Most disk pairs not coplanar | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Power law with exponential cutoff chosen for better outer cutoff description than a Gaussian, one fewer parameter than Nuker, and comparability with Long et al.  
  > "it has one less parameter than the Nuker profile, and the power-law exponent is not related to the exponential cutoff as it is in the similarity solution" (3 Analysis)
- Alternative: Gaussian, Nuker and self-similar profiles were considered; Gaussian and Nuker radii found compatible  
  > "both the $R_{\rm eff,dust}$ and $R_{\rm disk,dust}$ values are compatible with the results obtained using a Nuker profile" (3 Analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Uncertainties likely underestimated; gamma2 and T Tau S, UY Aur B, HN Tau B poorly constrained; no gas data  
  > "These uncertainties are likely underestimated." (3 Analysis)
- Caveat (inferred, ours): Comparison sample of singles is small (12) and processed in a companion paper
- Caveat (inferred, ours): K-S p-values with tiny values may be affected by correlated or non-independent samples and underestimated errors
- Caveat (inferred, ours): Dust optical depth and drift effects confound size comparison
- Caveat (inferred, ours): Projected separation used as proxy for semimajor axis
- Caveat (inferred, ours): Assumed gas/dust ratio of 2 taken from isolated Lupus disks

## Reproducibility

- Data public (paper): ALMA program 2016.1.00164.S cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00164.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibration details and self-cal parameters (in Long et al. 2019)
- Missing: MCMC priors
- Missing: Single-star comparison profiles from Long et al. 2019
- Data volume (inferred): ~tens of GB for 32-target snapshot survey (10 systems used)
- Score (inferred): 3/5, Method and sampler are described, but calibration, priors, and comparison sample live in companion papers.
- Rediscovery candidate: no, Calibration and comparison sample details are deferred to Long et al. 2019 and priors are not given.

## Links

- Method: (cite: tazzari18) (Galario visibility modelling)
- Method: (cite: AL94) (tidal truncation theory)
- Companion: (cite: long19) (Survey data reduction, single-disk comparison sample)
- Companion: (cite: long18) (Substructured disks including CIDA 9A and UZ Tau E fits)
- Related: ALMA Taurus disk structure survey (2016.1.00164.S)

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2016.1.00164.S"
 ],
 "obscore_codes_not_in_card": [
  "2016.1.01164.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 50,
  "rate": 0.595
 },
 "evidence_ok": true
}
```
