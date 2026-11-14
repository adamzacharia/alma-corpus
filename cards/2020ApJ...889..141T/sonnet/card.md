# A Noncorotating Gas Component in an Extreme Starburst at z = 4.3

`2020ApJ...889..141T` | The Astrophysical Journal 2020 | first author: Tadaki, Ken-ichi | arXiv: 2001.04638 | DOI: 10.3847/1538-4357/ab64f4

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Does the z=4.3 compact starburst SMG COSMOS-AzTEC-1 contain off-center gas components, and are they corotating with the disk (in-situ clumps vs. ex-situ accretion)?  
  > "we report the detection of a non-corotating subcomponent in a bright SMG at $z=4.3$, COSMOS-AzTEC-1" (Introduction)
- Target **COSMOS-AzTEC-1**: coordinates _not stated_; z/distance z=4.3  
  > "a bright unlensed submillimeter galaxy at $z=4.3$, COSMOS-AzTEC-1, hosting a compact starburst" (abstract); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01345.S, 2017.1.00127.S
- bands: Band 7, central frequency 350 GHz (860 um)  
  > "ALMA Band-7 observations of COSMOS-AzTEC-1 with a central frequency of 350 GHz (860 $\mu$m)" (Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: compact 15 m–2.5 km; extended 178 m–14.6 km  
  > "The compact and extended configuration observations cover the baseline lengths of 15 m – 2.5 km and 178 m – 14.6 km, respectively." (Data)
- angular resolution: 0.09'' (continuum and high-res cube), 0.17x0.16'' (low-res cube)  
  > "resulting in a spatial resolution of 0.$''$$17\times$0.$''$16" (Data)
- max recoverable scale: _not stated_
- sensitivity: 46 uJy/beam continuum; 0.40 and 0.45 mJy/beam per channel in low/high-res cubes  
  > "The noise levels in the low- and high-resolution cubes are 0.40 mJy beam$^{-1}$ per channel and 0.45 mJy beam$^{-1}$ per channel, respectively." (Data)
- time on source: ~30 min per configuration  
  > "The integration time is $\sim$30 minutes in both configurations." (Data)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: C+ [C II] 158 um (not stated)
- External data: Previous 0.3'' [C II] cube kinematic fit and CO(4-3) size, 1.1 mm source search  
  > "The kinematic parameters agree well with those derived from the previous fitting of a 0.3$''$-resolution \[C ii\] cube with a channel width of 50 km s$^{-1}$" (Analysis) [from (cite: 2019ApJ...876....1T)]
- External data: [C I]-based gas mass of 7.2e10 Msun within 2.5 kpc  
  > "the \[C i\]-based gas mass of $7.2\times10^{10}~M_\odot$ is mostly enclosed inside a radius of 2.5 kpc" (Discussion) [from (cite: 2018Natur.560..613T)]

## Processing

### Calibration

- pipeline or manual: standard CASA calibration  
  > "We calibrate the data in the standard manner using `CASA`" (Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean, concat, immoments  
  > "using the `CASA/tclean` task" (Data)
- deconvolver: Multi-Scale Clean  
  > "We also adopt `Multi-Scale Clean` algorithm" (Data)
- weighting robust: robust=+2.0 with uvtaper 0.05'' (continuum); robust=+2.0, uvtaper 0.1'' (low-res cube)  
  > "Cleaning with weighting of `robust`=+2.0 and `uvtaper`=0.$''$05 results in a spatial resolution of 0.$''$09$\times$0.$''$09" (Data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: circular mask 1'' diameter, cleaned to 1 sigma  
  > "We clean the map down to the 1$\sigma$ level in a circular mask with a diameter of 1$''$" (Data)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: concat in uv plane; compact weights scaled by 0.2 for continuum, unscaled for cubes  
  > "We decrease the absolute visibility weights of the compact data by 0.2" (Data)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CASA version
- cell and image size
- line-free channels / continuum subtraction for cubes
- flux calibrator and calibration details
- galpak3D MCMC settings and priors
- GALFIT initial guesses
- FAKEOBS parameters
- target coordinates

## Analysis recipe

1. **Make continuum map and cubes**: Combine compact and extended data; tclean with robust=+2 and taper; 30 km/s channels  
  > "we make low- and high-resolution clean cubes with a channel width of 30 km s$^{-1}$" (Data)
   - software: CASA
   - fitting: _not stated_
   - validation: Visibility amplitude comparison between configs (Appendix A)  
  > "There is no systematic offset in the amplitude of the vector-averaged visibilities between the compact and extended configuration data" (Data)
2. **Fit dust continuum disk and clumps**: Sersic (plus point source or Gaussian) fits with 7 free parameters; residual search  
  > "we fit single S$\acute{\mathrm{e}}$rsic models to the high-resolution 860 $\mu$m map using the `GALFIT` code" (3.1)
   - software: GALFIT
   - fitting: GALFIT least squares, sky fixed to zero, clean Gaussian beam as PSF  
  > "while the sky value is fixed to be zero" (3.1)
   - validation: FAKEOBS simulations of 300 maps  
  > "Six of 300 simulated residual maps show positive or negative 5$\sigma$ emission" (Appendix B)
3. **Fit [CII] disk kinematics and find residuals**: 3D thick disk with arctan rotation curve fit to low-res cube, subtract, search residual channel maps  
  > "We assume a thick disk and an arctan rotation curve in the models." (3.2)
   - software: Galpak3D
   - fitting: MCMC, 9 free parameters  
  > "are fitted to the data cube using a Markov chain Monte Carlo (MCMC) algorithm" (3.2)
   - validation: 100x3 simulated cubes and dirty cube analysis  
  > "Both \[C ii\]-1 and \[C ii\]-2 are detected at above $5\sigma$ in two channels" (Appendix C)
4. **Measure subcomponent fluxes**: Velocity-integrated maps over >2 sigma range; elliptical Gaussian fit  
  > "by using CASA/`imfit`, which fits an elliptical gaussian component on the image" (3.3)
   - software: CASA
   - fitting: imfit  
  > "We derive 0.17$\pm$0.04 Jy km s$^{-1}$ for \[C ii\]-1 and 0.62$\pm$0.10 Jy km s$^{-1}$ for \[C ii\]-2 by using CASA/`imfit`, which fits an elliptical gaussian component on the image." (Properties of the off-center components)
   - validation: _not stated_

## Software

- **CASA** : calibration, concat, tclean, immoments, imfit  
  > "We calibrate the data in the standard manner using `CASA`" (Data)
- **GALFIT** : Sersic fits to continuum  
  > "using the `GALFIT` code" (3.1)
- **Galpak3D** : kinematic disk fits to [CII] cube  
  > "by using the `Galpak3D` code" (3.2)
- **FAKEOBS** : simulating ALMA observations  
  > "we simulate ALMA observations of 860 $\mu$m continuum observations by using `FAKEOBS`" (Appendix B)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk S860 (single Sersic) | 17.50 | 0.74 | mJy | 2 | We derive $S_{860}=17.50\pm0.74$ mJy |
| Disk R1/2 (dust, single Sersic) | 1.22 | 0.07 | kpc | 2 | $R_{1/2}=1.22\pm0.07$ kpc |
| [CII] line flux | 13.31 | 0.32 | Jy km/s | 3 | $Sdv=13.31\pm0.32$ Jy km s$^{-1}$ |
| Vmax | 219 | 9 | km/s | 3 | $V_\mathrm{max}=219\pm9$ km s$^{-1}$ |
| sigma0 | 74 | 2 | km/s | 3 | $\sigma_0=74\pm2$ km s$^{-1}$ |
| [CII] R1/2 | 1.76 | 0.13 | kpc | 3 | $R_{1/2}=1.76\pm0.13$ kpc |
| [CII]-2 flux | 0.62 | 0.10 | Jy km/s | 4 | 0.62$\pm$0.10 Jy km s$^{-1}$ for \[C ii\]-2 |
| [CII]-1 flux | 0.17 | 0.04 | Jy km/s | 4 | We derive 0.17$\pm$0.04 Jy km s$^{-1}$ for \[C ii\]-1 |

## Qualitative findings

- [CII]-2 is offset by ~200 km/s, lies along the kinematic minor axis, 2 kpc from the disk; interpreted as infalling gas  
  > "The spatial and velocity offset suggest that \[C ii\]-2 is falling into COSMOS-AzTEC-1 from a direction perpendicular to the disk rotation." (3.3)

## Claim tuples

- H: Are there non-corotating gas components in the starburst disk? | E: Galpak3D disk fit to [CII] cube and residual channel maps, with simulations and dirty-cube checks | R: Two residual components above 5 sigma in two adjacent channels; [CII]-2 offset by ~200 km/s along minor axis | F: [CII]-2 is a non-corotating infalling component | **supported**
- H: Are low S/N dust clumps from earlier work real? | E: Sersic fits and residual map | R: Only two bright clumps recovered; other 8 not detected | F: Low S/N clumps may be noise artifacts | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): [CII]-1 could be an artifact of disk asymmetry; deeper observations needed  
  > "It requires deeper observations to distinguish whether or not \[C ii\] -1 truly represents a separate component from the overall disk rotation." (3.3)
- Caveat (inferred, ours): Single-pointing short integration; residual significance depends on idealized disk model
- Caveat (inferred, ours): Mass ratio inferred from [CII] flux ratio only

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and cell/image sizes
- Missing: Galpak3D and GALFIT configuration
- Missing: FAKEOBS settings
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Public data and named tools, but several imaging and fitting settings are missing.
- Rediscovery candidate: no, Key fitting details are not given and the main result is a qualitative residual detection.

## Links

- Method: (cite: 2015AJ....150...92B) (Galpak3D)
- Method: (cite: 2010AJ....139.2097P) (GALFIT)
- Companion: (cite: 2016ApJ...829L..10I) (Earlier ALMA data and clump identification)
- Companion: (cite: 2019ApJ...876....1T) (Earlier [CII] and CO data)

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 31,
  "rate": 0.492
 },
 "evidence_ok": true
}
```
