# ALMA Observations of the Young Substellar Binary System 2M1207

`2017AJ....154...24R` | The Astronomical Journal 2017 | first author: Ricci, L. | arXiv: 1706.03708 | DOI: 10.3847/1538-3881/aa78a0

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Do the brown dwarf 2M1207A and its planetary-mass companion 2M1207b host dust and gas disks, and what are their sizes and masses?  
  > "We detect emission from dust continuum at 0.89 mm and from the $J = 3 - 2$ rotational transition of CO from a very compact disk around the young brown dwarf." (abstract)
- Target **2M1207 (2MASS J12073346-3932539)**: coordinates _not stated_; z/distance 52.8 pc  
  > "2M1207A and b have an angular separation of 0.77$''$, which corresponds to a projected separation of 40.6 au at a distance of 52.8 pc (cite: Ducourant:2008)." (Introduction); distance from Ducourant et al. 2008; weighted mean of parallaxes (Gizis 2007, Biller 2007, Ducourant 2008)  
  > "2M1207A and b have an angular separation of 0.77$''$, which corresponds to a projected separation of 40.6 au at a distance of 52.8 pc (cite: Ducourant:2008)." (Introduction)

## Data provenance

- ALMA projects: 2013.1.01016.S
- bands: Band 7 (about 338 GHz)  
  > "We observed the 2M1207 system using ALMA Early Science in Cycle 2 at Band 7 (frequency of about 338 GHz)." (2 ALMA Observations and Data Reduction)
- frequencies and spectral setup: 4 spectral windows, 1.875 GHz each, centered 330.98, 332.93, 342.98, 344.98 GHz; 0.488 MHz channels (0.42 km/s), Hanning smoothed  
  > "Their central frequency is 330.98, 332.93, 342.98 and 344.98 GHz, respectively." (2 ALMA Observations and Data Reduction); "The channel width in these two spectral windows is 0.488 MHz (0.42 km s$^{-1}$ for CO $J = 3 - 2$)." (2 ALMA Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 19.6 to 650.3 m  
  > "Baseline lengths ranged between 19.6 and 650.3 m." (2 ALMA Observations and Data Reduction)
- angular resolution: 0.42'' x 0.35'' (22 x 18 au) in continuum  
  > "The angular resolution is $0.42'' \times 0.35''$ which corresponds to a spatial resolution of about 22 au $\times$ 18 au at the distance of 2M1207." (3.1 Continuum image)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 26 uJy/beam  
  > "the uncertainty accounts for a rms noise of 26 $\mu$Jy beam$^{-1}$" (3.1 Continuum image)
- time on source: about 2 hours  
  > "The total time on-source was approximately 2 hours." (2 ALMA Observations and Data Reduction)
- observing dates: June 29, July 17 and 18 2014  
  > "Observations were performed on June 29, July 17 and 18 2014, when 30 antennas were available." (2 ALMA Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated)
- External data: Dust opacity 3.4 cm2/g at 338 GHz  
  > "dust opacity $\kappa_{\nu} = 3.4$ cm$^2$ g$^{-1}$ at a frequency of 338 GHz (cite: Beckwith:1990)" (4 Analysis of the dust continuum emission) [from (cite: Beckwith:1990)]
- External data: Dust temperature relation T ~ 22 (L/Lsun)^0.16 K  
  > "$T_{\rm{vdP}} \approx 22 (L_{\star}/L_\odot)^{0.16}$ K" (4 Analysis of the dust continuum emission) [from (cite: vanderPlas:2016)]
- External data: 2M1207b luminosity ~1.5e-4 Lsun  
  > "$L_{\star,\rm{2Mb}} \approx 1.5 \times 10^{-4} L_\odot$ (cite: Skemer:2011)" (4 Analysis of the dust continuum emission) [from (cite: Skemer:2011)]

## Processing

### Calibration

- pipeline or manual: Calibrated by NRAO staff  
  > "The ALMA data were calibrated by National Radio Astronomy Observatory (NRAO) staff using the CASA software package version 4.2" (2 ALMA Observations and Data Reduction)
- casa version: CASA 4.2  
  > "using the CASA software package version 4.2" (2 ALMA Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan, Butler-JPL-Horizons 2012 models  
  > "The flux scale was determined with observations of Titan, and adopting the Butler-JPL-Horizon 2012 models" (2 ALMA Observations and Data Reduction)
- flux scale uncertainty: about 10%  
  > "resulting in an accuracy of about 10$\%$" (2 ALMA Observations and Data Reduction)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "The CASA task `clean` was used to Fourier invert the complex visibilities and deconvolve the interferometric dirty image." (3.1 Continuum image)
- deconvolver: _not stated_
- weighting robust: Continuum: natural, Briggs robust = 2; CO moment 0: robust = 0.5  
  > "natural weighting (Briggs robust parameter of 2) to maximize sensitivity" (3.1 Continuum image); "This was obtained with a Briggs robust parameter of 0.5 for the `clean` algorithm" (3.2 CO J = 3 - 2)
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

- Modeling framework for CO visibility fitting  
  > "Further description of the modeling framework can be found in (cite: Czekala:2015a)." (5 Analysis of the CO emission) [from (cite: Czekala:2015a)]
- Disk vertical structure for RADMC-3D model  
  > "disk vertical structure as in (cite: Skemer:2011)" (4 Analysis of the dust continuum emission) [from (cite: Skemer:2011)]
- Tidal truncation Monte Carlo method  
  > "we applied the Monte Carlo method presented by (cite: Harris:2012)" (6.2 Properties of the 2M1207A disk) [from (cite: Harris:2012)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum-subtraction details
- Image size, cell size, clean threshold and masks
- Velocity range/channel selection used for the CO moment 0 map and the fitted visibilities
- Stellar and disk parameters (e.g. fixed outer radius, scale height) in the DiskJockey runs
- MCMC priors on parameters other than gamma_e and q
- RADMC-3D setup (grain properties, photon counts)
- Gas/dust assumptions for the tidal truncation Monte Carlo

## Analysis recipe

1. **Image continuum and measure flux**: clean imaging and imfit Gaussian fit; upper limit at 2M1207b from 3 sigma assuming point source  
  > "a gaussian fit on the image plane using the CASA task `imfit` returns a point-like source convolved with the synthesized beam." (3.1 Continuum image)
   - software: CASA
   - parameter: robust = 2  
  > "natural weighting (Briggs robust parameter of 2) to maximize sensitivity" (3.1 Continuum image)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive dust masses**: Optically thin M=F d^2/(kappa B(T)); optically thick limit gives radius limit  
  > "$$\begin{equation} \label{eq:dust_mass} M_{\rm{dust}} = \frac{F_{\nu} d^{2}}{\kappa_{\nu}B_{\nu}(T_{\rm{dust}})}, \end{equation}$$" (4 Analysis of the dust continuum emission)
   - software: RADMC-3D
   - parameter: T_dust ~ 8 K  
  > "we therefore adopt this value for the characteristic temperature of the dust in this disk." (4 Analysis of the dust continuum emission)
   - assumption: d = 52.8 pc, kappa = 3.4 cm2/g at 338 GHz  
  > "With a distance $d = 52.8$ pc and dust opacity $\kappa_{\nu} = 3.4$ cm$^2$ g$^{-1}$ at a frequency of 338 GHz" (4 Analysis of the dust continuum emission)
   - fitting: _not stated_
   - validation: RADMC-3D disk model used to test the temperature estimate  
  > "To test this estimate, we generated a representative disk model with the radiative transfer code `RADMC-3D`" (4 Analysis of the dust continuum emission)
3. **Fit CO visibilities for disk structure and dynamical mass**: Parametric disk model, RADMC-3D channel maps sampled at the uv positions, chi2 fit in visibility space  
  > "Raw channel maps of the disk are synthesized using `RADMC-3D` (cite: Dullemond:2012), Fourier transformed, and then sampled in the $u-v$ plane at the baselines corresponding to the ALMA observations" (Analysis of the CO emission of the 2M1207A disk)
   - software: DiskJockey, RADMC-3D, emcee
   - parameter: gamma = 1; q between 0 and 3/4; gamma_e <= 2  
  > "We explore surface density profiles with a power law exponent of $\gamma = 1$." (5 Analysis of the CO emission)
   - assumption: distance prior 52.8 ± 1.0 pc  
  > "we proceed to fit the source using a distance prior of $d = 52.8 \pm 1.0\,\textrm{pc}$" (5 Analysis of the CO emission)
   - fitting: Affine-invariant ensemble MCMC, 48 walkers, 10,000 iterations, 5,000 burn-in  
  > "with 48 walkers run for 10,000 iterations. After the first 5,000 iterations were discarded for burn-in" (5 Analysis of the CO emission)
   - validation: Autocorrelation time 80 iterations; data/model/residual channel maps  
  > "we computed the autocorrelation time to be 80 iterations" (5 Analysis of the CO emission)
4. **Test tidal truncation**: Monte Carlo of truncation radius from projected separation and mass ratio, using Artymowicz & Lubow fits for alpha 0.1-0.0001, uniform orbital priors  
  > "we fit the results from the (cite: Artymowicz:1994) tidal truncation models for different values of the viscosity $\alpha$-parameter chosen between 0.1 and 0.0001." (6.2 Properties of the 2M1207A disk)
   - assumption: 2M1207b orbit possibly in the disk plane  
  > "If we assume that the orbit of 2M1207b lies on the plane of the 2M1207A disk" (6.2 Properties of the 2M1207A disk)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2: calibration, clean imaging, imfit  
  > "using the CASA software package version 4.2" (2 ALMA Observations and Data Reduction)
- **DiskJockey** : forward-modeling CO visibilities  
  > "We use the `DiskJockey` package" (5 Analysis of the CO emission)
- **RADMC-3D** : dust temperature test and CO channel map synthesis  
  > "we generated a representative disk model with the radiative transfer code `RADMC-3D`" (4 Analysis of the dust continuum emission)
- **emcee** : MCMC ensemble sampler (Goodman & Weare; Foreman-Mackey et al.)  
  > "Markov Chain Monte Carlo (MCMC) ensemble sampler (cite: Goodman:2010; Foreman:2013)" (5 Analysis of the CO emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 2M1207A continuum flux density at 0.89 mm | 620 | 67 | uJy | 1 | The flux density from the disk is $620 \pm 67$ $\mu$Jy |
| 2M1207b 3 sigma flux upper limit | 78 | not stated | uJy | 1 | The $3\sigma$ upper limit for the flux density at 0.89 mm is 78 $\mu$Jy |
| 12CO J=3-2 integrated flux of 2M1207A | 71.0 | 8.4 | mJy km/s | 1 | velocity-integrated total flux of $71.0 \pm 8.4$ mJy km s$^{-1}$ |
| 2M1207b dust mass upper limit | <0.013 M_earth (~1.1 M_Moon) | not stated | M_earth | 2 | $M_{\rm{dust},\rm{2Mb}} < 0.013~M_\oplus \approx 1.1~M_{\rm{Moon}}$ |
| 2M1207A dust mass | ~0.1 | not stated | M_earth | 2 | the dust mass for the detected 2M1207A disk is $M_{\rm{dust},\rm{2MA}} \approx 0.1~M_\oplus$ |
| Characteristic radius of CO disk | 9.4 | 1.5 | au | 3 | Characteristic radius (au) / 9.4 $\pm$ 1.5 |
| Dynamical mass of 2M1207A | 60 | +80/-20 | M_Jup | 3 | $M_\ast = 60^{+80}_{-20}\,M_{\rm{Jup}}$ |
| Disk inclination | 35 | +20/-15 | deg | 3 | Disk inclination (${}^\circ$) / 35$^{+20}_{-15}$ |
| Disk position angle | 174 | 12 | deg | 3 | Disk position angle$^{a}$ (${}^\circ$) / 174 $\pm$ 12 |
| Current physical separation (coplanar assumption) | 42 | +19/-2 | au | 4 | we derived an estimate of $42^{+19}_{-2}$ au for the current separation |

## Qualitative findings

- No dust or CO emission at 2M1207b; 2M1207A dust emission unresolved  
  > "Neither dust emission nor CO J=3-2 line emission were detected at the location of the planetary-mass companion 2M1207b." (Conclusions)

## Claim tuples

- H: Does 2M1207b host a massive circum-planetary dust disk? | E: 0.89 mm continuum non-detection converted to dust mass | R: <0.013 M_earth (~1.1 M_Moon) | F: Tightest dust limit for a young planetary-mass companion; little mm pebble material | **supported**
- H: Is the 2M1207A disk compact due to tidal truncation by 2M1207b? | E: CO uv-plane fit and Monte Carlo truncation model | R: r_c = 9.4 ± 1.5 au; truncation radius ≳10 au for e ≲ 0.4 | F: Tidal truncation can naturally explain small radius, though independent formation is not ruled out | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): CO disk only marginally resolved, giving M sin^2 i degeneracy  
  > "The ALMA CO observations spatially resolve the 2M1207A disk only marginally." (5 Analysis of the CO emission)
- Caveat (inferred, ours): Dust temperature of 8 K and the Beckwith opacity dominate the mass limits
- Caveat (inferred, ours): Dynamical mass poorly constrained due to inclination degeneracy
- Caveat (inferred, ours): Temperature parameters unconstrained by the data

## Reproducibility

- Data public (paper): ALMA project 2013.1.01016.S cited in the acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.01016.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: DiskJockey freely available on GitHub (MIT license)  
  > "Freely available at <https://github.com/iancze/DiskJockey> under an open-source MIT license." (footnote 1)
- Missing: Imaging parameters (cell/image size, masks, thresholds)
- Missing: Exact DiskJockey configuration and priors
- Missing: Line-free channels
- Data volume (inferred): ~10-30 GB for 3 execution blocks
- Score (inferred): 6/5, Public data and simple analysis, but imaging and modeling settings are incompletely given.
- Rediscovery candidate: yes, Public data, a numeric continuum flux and mass limits are reproducible; the CO model is partly specified.

## Links

- Method: (cite: Czekala:2015a) (DiskJockey modeling framework)
- Method: (cite: Harris:2012) (tidal truncation Monte Carlo method)

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
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
  "facts": 74,
  "stated": 43,
  "rate": 0.581
 },
 "evidence_ok": true
}
```
