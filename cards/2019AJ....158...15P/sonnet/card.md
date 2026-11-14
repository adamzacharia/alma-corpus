# Dust Unveils the Formation of a Mini-Neptune Planet in a Protoplanetary Ring

`2019AJ....158...15P` | The Astronomical Journal 2019 | first author: Pérez, Sebastián | arXiv: 1902.05143 | DOI: 10.3847/1538-3881/ab1f88

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Can the fine triple-ring structure in the outer disk of HD 169142 be explained by a single migrating low-mass planet?  
  > "to test whether the three bright rings (B2, B3, B4) unveiled by our ALMA observations can be explained by a single forming planet." (3.2 Physical model and numerical setup)
- Target **HD 169142**: coordinates _not stated_; z/distance 113.9±0.8 pc  
  > "for a distance to HD 169142 of 113.9$\pm$0.8 pc (cite: Gaia2018)" (2.2 A triple ring system in the disk’s outer region); distance from Gaia (Gaia2018)  
  > "for a distance to HD 169142 of 113.9$\pm$0.8 pc (cite: Gaia2018)" (2.2 A triple ring system in the disk’s outer region)

## Data provenance

- ALMA projects: 2016.1.00344.S
- bands: 1.3 mm continuum  
  > "We obtained 1.3 millimeter observations by combining ALMA 12-m array extended (C40-9) and more compact (C40-6) configurations" (2 Observations and data reduction)
- frequencies and spectral setup: Two 1.875 GHz continuum spectral windows centred at 232.0 and 218.0 GHz, FDM  
  > "Two spectral windows with 1.875 GHz bandwidth were set up for detecting the dust continuum, centred at 232.0 GHz and 218.0 GHz, respectively." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 19 m to 13.9 km, 40-46 antennas  
  > "resulting in baselines ranging from 19 meters to up to 13.9 kilometers and a total of 40-46 antennas." (2 Observations and data reduction)
- angular resolution: _not stated_
- max recoverable scale: 2.0 arcsec  
  > "The combined observations are sensitive to spatial scales of up 2.0$''$, with a spatial resolution of $\sim$20 mas." (2 Observations and data reduction)
- sensitivity: rms 14.7 µJy/beam in MEM image  
  > "an rms ($1\sigma$) of 14.7$\mu$Jy beam$^{-1}$ for a synthesized beam of 27$\times$20 mas" (2.1 ALMA continuum imaging)
- time on source: _not stated_
- observing dates: Sept.-Nov. 2017 (Cycle 4) long baseline, four blocks of ~40 min  
  > "The long baseline observations were acquired between Sept. and Nov. 2017 (Cycle 4) in four different blocks of $\sim$40 min each." (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Other facility **Gaia**: Distance to HD 169142 and stellar parameters  
  > "for a distance to HD 169142 of 113.9$\pm$0.8 pc (cite: Gaia2018)" (2.2 A triple ring system in the disk’s outer region)
- External data: Radiative transfer parameterisation of inner disk and ring B1, and surface density normalisation  
  > "Their parameterisation follows previous RT modelling which fits the 1.3 millimeter data (cite: Fedele2017)." (3.2.2 Radiative transfer calculation) [from Fedele et al. 2017 (cite: Fedele2017)]
- External data: Stellar proper motion from SIMBAD  
  > "consistent with the (-2.8,-38.0) mas/yr proper motion listed for this star (SIMBAD)" (2 Observations and data reduction) [from SIMBAD]
- Simulation/model as data: 2D Dusty FARGO-ADSG hydro simulation with 11 Earth-mass (~10) planet, then RADMC-3D synthetic image compared to ALMA  
  > "Our 2D hydrodynamical simulation of the gas and dust in the HD 169142 disk has been carried out with the code Dusty FARGO-ADSG." (3.2.1 Hydrodynamical simulations)

## Processing

### Calibration

- pipeline or manual: ALMA Pipeline by ALMA staff in CASA  
  > "All data were calibrated by the ALMA staff using the ALMA Pipeline version 40896 in the CASA package (cite: McMullin2007)" (2 Observations and data reduction)
- casa version: _not stated_
- pipeline version: 40896  
  > "All data were calibrated by the ALMA staff using the ALMA Pipeline version 40896" (2 Observations and data reduction)
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10%  
  > "(10% flux calibration uncertainty)" (2.1 ALMA continuum imaging)
- self calibration: single iteration of phase-only, before concat  
  > "Self-calibration of the data was performed to improve coherence (a single iteration of phase-only)" (2 Observations and data reduction)

### Imaging

- task: tclean (CASA 5.2) and MEM with GPUVMEM; MEM image adopted  
  > "Image reconstruction was initially performed using the CLEAN algorithm (CASA version 5.2, task `tclean`)." (2.1 ALMA continuum imaging); "We adopted the MEM image for our analysis." (2.1 ALMA continuum imaging)
- deconvolver: Maximum entropy regularised by minimizing the Laplacian of the model image  
  > "regularized by minimizing the Laplacian of the model image with an objective function." (2.1 ALMA continuum imaging)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: concat of short and long baseline datasets after 20,40 mas offset correction  
  > "after which they were combined using the CASA task concat." (2 Observations and data reduction)
- smoothing: _not stated_
- final beam: 27x20 mas  
  > "for a synthesized beam of 27$\times$20 mas" (2.1 ALMA continuum imaging)
- final rms: 14.7 µJy/beam  
  > "an rms ($1\sigma$) of 14.7$\mu$Jy beam$^{-1}$" (2.1 ALMA continuum imaging)

### Inherited from earlier work

- Inner disk and B1 parameterisation in RT model  
  > "Their parameterisation follows previous RT modelling which fits the 1.3 millimeter data (cite: Fedele2017)." (3.2.2 Radiative transfer calculation) [from Fedele2017]
- Gap-separation relation informed by hydrodynamic calculations  
  > "Informed by hydrodynamic calculations (cite: Dong2018), the relation reads" (3.1 Theoretical background) [from Dong2018]

### Not stated but needed to reproduce (our reading)

- Robust/weighting, cell size, image size and masks for tclean images
- GPUVMEM parameters (regularisation weight, lambda, iterations, prior)
- Which ALMA execution blocks/datasets were used for the short baseline configuration
- Dusty FARGO-ADSG code is only available on request
- Self-calibration solution interval and reference antenna
- Dust opacity data used in RADMC-3D

## Analysis recipe

1. **Calibrate and combine data**: ALMA pipeline, one round phase-only self-cal, offset correction, concat  
  > "A positional offset of (-20,-40) mas between the short and long baseline resulting images was measured and corrected prior to combining the datasets." (2 Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Image continuum with MEM**: Super-resolution MEM imaging with GPUVMEM, compared with CLEAN  
  > "we super-resolve the continuum data using our Maximum Entropy Method (MEM) package uvmem" (2.1 ALMA continuum imaging)
   - software: GPUVMEM, CASA tclean
   - fitting: _not stated_
   - validation: Triple ring structure robust in all reconstructions  
  > "The triple ring structure in the outer region is robust in all image reconstructions." (Comparison between CLEAN and MEM algorithm)
3. **Measure ring locations and widths**: Deproject by inclination, azimuthally average, fit three Gaussians plus polynomial; deconvolve beam  
  > "Three Gaussian components were fit simultaneously plus a common low-order polynomial to account for low level background emission." (2.2 A triple ring system in the disk’s outer region)
   - parameter: i = 12.5±0.5 deg  
  > "we deproject the image by the disk inclination angle $i$ = $12.5^\circ$$\pm$0.5$^\circ$" (2.2 A triple ring system in the disk’s outer region)
   - fitting: Simultaneous Gaussians plus polynomial  
  > "Three Gaussian components were fit simultaneously plus a common low-order polynomial to account for low level background emission." (A triple ring system in the disk’s outer region)
   - validation: _not stated_
4. **Fit ring eccentricity**: Gaussian fits in radius per azimuth, direct least-squares ellipse fit, Monte Carlo errors (1000 repeats)  
  > "The ellipse equation is then fitted to $R(\theta)$ for a given ring using a direct least square procedure (cite: Fitzgibbon1996)." (Polar deprojection and ellipse fitting)
   - software: iminuit
   - parameter: Only signal above 5 sigma used; inclination explored 9-16 deg  
  > "Only signal above $5\sigma$ is included in the process." (Polar deprojection and ellipse fitting)
   - fitting: Least-squares ellipse; Monte Carlo errors  
  > "The ellipse equation is then fitted to $R(\theta)$ for a given ring using a direct least square procedure" (Polar deprojection and ellipse fitting)
   - validation: Common inclination where B2 and B3 eccentricities coincide  
  > "This fitting procedure thus suggests a common inclination for both B2 and B3 of $i$$\approx$$12.5^\circ\pm0.5\deg$ (1$\sigma$)." (Polar deprojection and ellipse fitting)
5. **Hydrodynamic simulation of migrating planet**: 2D gas plus Lagrangian dust simulation with 11 Earth-mass planet at 69 au, alpha=1e-5, 200,000 dust particles  
  > "The code solves the equations of motion for 200,000 dust particles with radii between 10 $\mu$m and 3 mm." (3.2.1 Hydrodynamical simulations)
   - software: Dusty FARGO-ADSG
   - parameter: 900x1200 cells, 35-105 au; alpha 1e-5; h/r 0.033 at 69 au  
  > "The $\alpha$ turbulent viscosity is set to $10^{-5}$." (3.2.1 Hydrodynamical simulations)
   - assumption: Gas surface density 2.9 g cm-2 at 100 au; locally isothermal, 8 K at 70 au  
  > "The initial surface density is 2.9 g cm$^{-2}$ at 100 au" (3.2.1 Hydrodynamical simulations)
   - fitting: Parameter sampling, no exhaustive fit  
  > "no exhaustive exploration is intended as finding a perfect fit is not in the scope of this work." (3.2.1 Hydrodynamical simulations)
   - validation: Compare ring locations and fluxes to ALMA image  
  > "The hydrodynamical model reproduces the locations of B2, B3, and B4 as well as the level of flux along rings B2 and B3, and to a lesser extend ring B4’s." (Radiative transfer calculation)
6. **Synthetic image via radiative transfer**: RADMC-3D thermal Monte Carlo and ray tracing, convolved with MEM beam  
  > "The resulting synthetic image is convolved with the MEM resolution beam" (3.2.2 Radiative transfer calculation)
   - software: RADMC-3D
   - parameter: n(s)∝s^-3.5, 1 µm-1 mm; 1e8 photon packages; D_z=10 alpha  
  > "A $D_z$ value equal to 10 $\alpha$ yields dust temperatures which match the observed brightness temperature of rings B2 and B3." (3.2.2 Radiative transfer calculation)
   - assumption: gas-to-dust 33; 30% amorphous carbon, 70% silicates; star 7320 K, 1.5 Rsun  
  > "Assuming a gas-to-dust ratio of 33 yields a total dust mass in the outer region of $\sim$100$M_\oplus$." (3.2.2 Radiative transfer calculation)
   - fitting: _not stated_
   - validation: Model reproduces B2-B4 locations and B2, B3 flux  
  > "The hydrodynamical model reproduces the locations of B2, B3, and B4 as well as the level of flux along rings B2 and B3" (3.2.2 Radiative transfer calculation)

## Software

- **CASA** 5.2 (tclean); pipeline 40896: Calibration, concat, CLEAN imaging  
  > "CLEAN algorithm (CASA version 5.2, task `tclean`)" (2.1 ALMA continuum imaging)
- **GPUVMEM** : MEM imaging  
  > "Here we used the publicly-available GPU adaptation GPUVMEM" (2.1 ALMA continuum imaging)
- **Dusty FARGO-ADSG** : Hydrodynamic simulation of gas and dust  
  > "carried out with the code Dusty FARGO-ADSG" (3.2.1 Hydrodynamical simulations)
- **RADMC-3D** 0.41: Continuum radiative transfer  
  > "the public radiative transfer (RT) code radmc3d (version 0.41)" (3.2.2 Radiative transfer calculation)
- **iminuit** : Gaussian fits in radius per azimuth  
  > "(using the Python `iminuit` optimization library)" (Polar deprojection and ellipse fitting)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Ring B2 radius | 0.503 arcsec (57.3 au) | 0.005 arcsec | arcsec | 3 | 0.503$''$$\pm$0.005$''$ (57.3  au) |
| Ring B3 radius | 0.563 arcsec (64.2 au) | 0.005 arcsec | arcsec | 3 | 0.563$''$$\pm$0.005$''$ (64.2 au) |
| Ring B4 radius | 0.667 arcsec (76.0 au) | 0.009 arcsec | arcsec | 3 | 0.667$''$$\pm$0.009$''$ (76.0 au) |
| Deconvolved widths B2, B3, B4 | 1.5, 1.8, 3.4 | not stated | au | 3 | Rings B2 and B3 have deconvolved widths of only 1.5 and 1.8 au, respectively, while B4 is more radially extended with a deconvolved width of 3.4  au. |
| Ring eccentricity | 0.09 | ±0.03 (main text); ±0.02 (2σ, appendix) | dimensionless | 4 | all three outer rings have a finite eccentricity (0.09$\pm$0.03) |
| Total flux density at 1.3 mm | 178 | 18 | mJy | 2 | The total flux density over the whole image is 178$\pm$18 mJy |
| Planet mass in model | ~10 (11 for 2 Msun, 9.6 for 1.7 Msun) | not stated | Earth masses | 5 | which for a 2 $M_\odot$ star translates into 11 $M_{\oplus}$ |
| Dust mass in outer region | ~100 | not stated | Earth masses | 6 | yields a total dust mass in the outer region of $\sim$100$M_\oplus$ |

## Qualitative findings

- Outer disk resolved into three narrow rings; the disk hosts both wide gaps and a narrow-ring system  
  > "The new ALMA high resolution images allow for the outer ring to be resolved as three narrow rings." (abstract)

## Claim tuples

- H: A single migrating low-mass planet can produce the triple ring system with asymmetric separations | E: 2D hydro plus RT of a 10 Earth-mass planet migrating from 69 to 64 au | R: Model reproduces ring locations and fluxes of B2 and B3, B4 slightly brighter | F: Inward migration of a mini-Neptune explains the asymmetric separations | **supported**
- H: Outer rings are eccentric | E: Ellipse fits to ring radii vs azimuth | R: e = 0.09±0.03 with common focus | F: All three outer rings have finite eccentricity | **supported**
- H: An inner giant planet could create the outer rings | E: Added 0.5 MJup planet at 38 au | R: Giant opens a gap but creates no additional narrow rings; induces eccentricity | F: Inner giant does not explain the triple ring | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Two low-mass planets, one per gap, rejected as requiring too small scale heights and likely a common gap  
  > "if you put two planets into the two gaps, they will likely open one common gap instead of two." (3.4.1 Could rings B2, B3 and B4 be shaped by two low-mass planets?)
- How they decided it was enough: _not stated_
- Limitation (authors): Not an exhaustive fit; no dust growth, fragmentation or back-reaction  
  > "Finding a perfect fit to the data is not in the scope of this work." (3.4.2 How does an inner giant planet impact the structure of rings B2, B3 and B4?)
- Caveat (inferred, ours): Planet mass is degenerate with assumed temperature, viscosity and dust size distribution
- Caveat (inferred, ours): Ring B4 detected only at 4-5 sigma
- Caveat (inferred, ours): MEM super-resolution may introduce artefacts in narrow ring widths
- Caveat (inferred, ours): Migration direction inference depends on assumed initial dust profile

## Reproducibility

- Data public (paper): Project code given; data in ALMA archive  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00344.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: GPUVMEM public on GitHub; FARGO-ADSG public; Dusty version on request  
  > "The version including a Lagrangian treatment of the dust particles, Dusty FARGO-ADSG, can be made available upon request to co-author Clement Baruteau." (Footnote 2)
- Missing: MEM parameters
- Missing: Dusty FARGO-ADSG code only on request
- Missing: imaging weighting and tclean settings
- Data volume (inferred): ~100-300 GB raw for long and short baseline Cycle 4 data
- Score (inferred): 5/5, Public data and the ring measurements are reproducible, but MEM settings and the dusty hydro code are not fully given.
- Rediscovery candidate: no, MEM imaging parameters are not stated and the modelling needs a code available only on request.

## Links

- Method: Cárcamo et al. 2018 (cite: Carcamo2018) (GPUVMEM MEM imaging code)
- Method: Dong et al. 2018 (cite: Dong2018) (Gap separation vs planet mass relation)
- Companion: Fedele et al. 2017 (cite: Fedele2017) (Previous 1.3 mm and RT model of HD 169142)
- Related: DSHARP

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 53,
  "rate": 0.646
 },
 "evidence_ok": true
}
```
