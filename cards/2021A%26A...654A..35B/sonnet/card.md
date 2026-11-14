# A multiwavelength analysis of the spiral arms in the protoplanetary disk around WaOph 6

`2021A&A...654A..35B` | Astronomy and Astrophysics 2021 | first author: Brown-Sevilla, S. B. | arXiv: 2107.13560 | DOI: 10.1051/0004-6361/202140783

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks
- Question: What is the morphology of the WaOph 6 disk in NIR scattered light versus ALMA mm continuum, and can a planetary perturber explain the spiral arms?  
  > "We aim to perform an in-depth characterization of the protoplanetary disk morphology around WaOph 6 analyzing data obtained at different wavelengths, as well as to investigate the origin of the spiral features in the disk." (abstract)
- Target **WaOph 6**: coordinates _not stated_; z/distance 122.5 pc  
  > "WaOph6 is a K6 star (cite: Eisner2005), and member of the Ophiuchus moving group at a distance of 122.5 $^{+0.3}_{-0.2}$ pc (cite: Gaia2020)" (2 Stellar and disk properties); distance from Gaia (cite: Gaia2020)  
  > "WaOph6 is a K6 star (cite: Eisner2005), and member of the Ophiuchus moving group at a distance of 122.5 $^{+0.3}_{-0.2}$ pc (cite: Gaia2020)" (2 Stellar and disk properties)

## Data provenance

- ALMA projects: 2016.1.00484.L
- bands: Band 6 (1.3 mm), 239 GHz  
  > "WaOph 6 was observed within ALMA/DSHARP (cite: Andrews2018) in Band 6, at a frequency of 239 GHz (1.3 mm)." (4.3 Comparison to ALMA Observations)
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
- pi or archival as stated: Archival ALMA-DSHARP data  
  > "compare them to archival millimeter continuum ALMA observations" (abstract)
- Other facility **VLT/SPHERE IRDIS-DPI**: H-band polarimetric scattered light images, PSF FWHM ~51 mas  
  > "We measure a point spread function (PSF) FWHM of $\sim$51 mas by fitting a Gaussian function to the flux frames." (3 Observations and data reduction)
- Other facility **HST**: archival 1999 epoch for companion astrometry  
  > "We used archival HST data (from 1999-01-23) as an additional epoch" (4.2 Companion candidate)
- External data: Disk inclination 47.3 deg and PA 174.2 deg from ellipse fitting  
  > "The disk has an inclination ($i$) of 47.3$^{\circ}$ and a position angle (PA) of 174.2$^{\circ}$ obtained from ellipse fitting on the dust continuum emission (cite: Huang2018)" (2 Stellar and disk properties) [from (cite: Huang2018)]
- External data: Calibrated DSHARP continuum visibilities  
  > "We start from the calibrated visibilities of the dust continuum emission, available from the DSHARP data release." (10 Appendix) [from (cite: Andrews2018)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: DSHARP calibrated visibilities used  
  > "We start from the calibrated visibilities of the dust continuum emission, available from the DSHARP data release." (10 Appendix)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean in CASA 5.4.1  
  > "we used two different images generated using the `tclean` task in CASA 5.4.1 (cite: McMullin2007)" (4.3.2 Spiral arms)
- deconvolver: _not stated_
- weighting robust: robust -1.0 and 1.0  
  > "and two different robust values (-1.0 and 1.0) to generate an image with higher resolution in the central and in the outer regions, respectively." (4.3.2 Spiral arms)
- uv taper: ['0.010arcsec','0.010arcsec','10deg']  
  > "We used uv-taper = \[‘0.010arcsec’, ‘0.010arcsec’, ‘10deg’\]" (4.3.2 Spiral arms)
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

- Non-axisymmetric extraction of ALMA visibilities follows earlier procedure  
  > "we follow a similar procedure to the one described in the Appendix B of (cite: Isella2019)" (10 Appendix) [from (cite: Isella2019)]
- MCMC spiral-fitting code based on emcee  
  > "we used the MCMC code based on `emcee` (cite: Foreman-Mackey2013) and described in (cite: Kurtovic2018)" (4.3.2 Spiral arms) [from (cite: Kurtovic2018)]

### Not stated but needed to reproduce (our reading)

- frank hyperparameters
- Pixel size and image size for ALMA tclean images
- Clean masks and threshold
- Exact peak-search parameters for spiral tracing
- Priors' bounds for spiral fits

## Analysis recipe

1. **Trace spirals in ALMA and SPHERE data**: Peak search along radial direction on tclean images (3 sigma) and peak_local_max on deprojected polar SPHERE image  
  > "Then, we searched for peak emission points along the radial direction and took the 3$\sigma$ emission ones as the spiral arms." (4.3.2 Spiral arms)
   - software: CASA, skimage, frank
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit spiral pitch angles**: Logarithmic and Archimedean spiral models fitted with emcee, i and PA fixed  
  > "To test the symmetry of the spiral arms, the parameters $r_0$ and $b$ were fitted separately, while we assumed $i$ and PA to be fixed" (4.3.2 Spiral arms)
   - software: emcee
   - parameter: 250 walkers, burn-in 1000+500 steps, 1500 sampling steps  
  > "we used 250 walkers with two consecutive burning stages of 1000 and 500 steps, and then 1500 steps to sample the parameter space." (4.3.2 Spiral arms)
   - fitting: emcee, flat priors  
  > "A flat prior probability is used for the free parameters." (4.3.2 Spiral arms)
   - validation: _not stated_
3. **Hydro + radiative transfer test of planet perturber**: PLUTO 3D gas and FARGO3D 2D gas+dust simulations, then RADMC-3D and CASA simobserve/tclean synthetic ALMA images  
  > "we performed 3D gas-only and 2D gas+dust hydrodynamical simulations in which a massive planet at a separations $\geq 90$ au generates large-scale spiral arms interior to its orbit." (5 Modeling)
   - software: PLUTO, FARGO3D, RADMC-3D, CASA, optool
   - fitting: _not stated_
   - validation: visual comparison to observed spirals  
  > "The obtained images resemble the ones detected both in the scattered light and millimeter continuum observations, except for the fact that we are only able to fit either the inner or the outer spirals" (Results and comparison to observations)

## Software

- **CASA** 5.4.1 (imaging); 5.6 (simulated obs): tclean imaging of DSHARP data; simobserve for synthetic observations  
  > "generated using the `tclean` task in CASA 5.4.1" (4.3.2 Spiral arms)
- **frank** : remove axisymmetric component from ALMA visibilities  
  > "we used the `frank` (cite: Jennings2020) tool to remove the azimuthally component of the emission of the disk" (4.3.2 Spiral arms)
- **emcee** : spiral fit MCMC  
  > "we used the MCMC code based on `emcee`" (4.3.2 Spiral arms)
- **RADMC-3D** : synthetic scattered light and mm images  
  > "using the radiative transfer code RADMC-3D" (5.2 Radiative transfer)
- **IRDAP** 1.3.2: SPHERE data reduction  
  > "we used the IRDAP pipeline[^4] version 1.3.2." (3 Observations and data reduction)
- **PLUTO** : 3D gas hydrodynamics  
  > "we ran 3D simulations of the gas dynamics using the hydrodynamical code `PLUTO`" (5.1 Hydrodynamical models)
- **FARGO3D** : 2D multi-fluid gas+dust simulations  
  > "using the multi-fluid version of the code `FARGO3D`" (5.1 Hydrodynamical models)
- **photutils** : elliptical annuli radial profiles  
  > "we use the `aperture_photometry()` function from the `photutils` python package" (4.3.1 Radial profiles)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spiral arm contrast in SPHERE Qphi | 1.5 | not stated | dimensionless | 0 | On average, we find the spiral arm contrast to be 1.5. |
| Log pitch angle ALMA S2 | 9.09 | +0.21/-0.10 | deg | 2 | S2 / 9.09$_{-0.10}^{+0.21}$ |
| Toomre Q range | 2.2-33.2 | not stated | dimensionless | 0 | We obtained that $Q$ varies from $2.2 -33.2$ from the outer part of the disk inward. |
| Dust mass | 1.4e-4 | not stated | Msun | 0 | Dust mass / 1.4x$10^{-4}$ M$_\odot$ / f |

## Qualitative findings

- Spirals are seen in scattered light and mm continuum; youngest disk with scattered-light spirals  
  > "making it the youngest disk with spiral arms detected at these wavelengths" (abstract)

## Claim tuples

- H: Spiral arms are driven by a planet rather than GI | E: Toomre Q estimate and hydro+RT simulations | R: Q>2.2 everywhere; 10 MJup planet at 140 au reproduces spirals | F: A planet of at least ~10 MJup could drive spirals | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gravitational instability disfavored by Toomre Q; companion candidate found to be background object  
  > "This indicates that the disk is fairly stable according to the Toomre stability criterion" (4.4 Origin of the spirals)
- How they decided it was enough: _not stated_
- Limitation (authors): Simulations cannot reproduce the spiral break, gap and ring  
  > "This is likely due to missing physics in our simulations" (5.3)
- Caveat (inferred, ours): Toomre estimate depends on assumed surface density profile and mass
- Caveat (inferred, ours): No quantitative fit metric between simulations and data

## Reproducibility

- Data public (paper): DSHARP data release  
  > "available from the DSHARP data release" (10 Appendix)
- Products in archive: _not stated_
- Missing: frank settings
- Missing: Clean parameters
- Missing: Hydro setup details such as planet-mass/disk-mass specifics
- Data volume (inferred): ~10 GB (DSHARP continuum)
- Score (inferred): 4/5, ALMA part is minor and settings incomplete; SPHERE data and simulations dominate.
- Rediscovery candidate: no, Main results depend on SPHERE data and custom simulations.

## Links

- Method: (cite: Isella2019) (Non-axisymmetric extraction procedure)
- Method: (cite: Kurtovic2018) (Spiral MCMC fitting code)
- Companion: (cite: Huang2018III) (DSHARP spiral analysis of WaOph 6)
- Companion: (cite: Andrews2018) (DSHARP survey)
- Related: DSHARP
- Related: DISK/SHINE

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 33,
  "rate": 0.471
 },
 "evidence_ok": true
}
```
