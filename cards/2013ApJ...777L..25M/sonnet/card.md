# ALMA Continuum Observations of a 30 Myr Old Gaseous Debris Disk around HD 21997

`2013ApJ...777L..25M` | The Astrophysical Journal Letters 2013 | first author: Moór, A. | arXiv: 1310.5069 | DOI: 10.1088/2041-8205/777/2/L25

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks, protoplanetary_disks
- Question: What is the distribution and origin of the dust in the gaseous debris disk around HD 21997, and how does it relate to the CO gas?  
  > "study the distribution and origin of the dust and its connection to the gas" (abstract)
- Target **HD 21997**: coordinates _not stated_; z/distance 72 pc  
  > "At a distance of 72 pc, HD 21997 belongs to the 30-Myr-old Columba association" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00780.S
- bands: four 2 GHz spectral windows around 345 GHz (effective wavelength 886 um)  
  > "Four spectral windows with bandwidth of 2 GHz each were defined around 345  GHz." (2.1 ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: Cycle 0, compact configuration, 15 antennas  
  > "in a compact configuration using 15 antennas" (2.1 ALMA observations)
- configurations: _not stated_
- baselines: 18.3 m to 134.2 m  
  > "offering baselines from 18.3m to 134.2m" (2.1 ALMA observations)
- angular resolution: 1.56x1.26 arcsec, PA -53.4 deg  
  > "a beam size of 1$\ensuremath{''}$56$\times$1$\ensuremath{''}$26" (2.1 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: 4.5e-2 mJy/beam rms  
  > "typical r.m.s noise of 4.5$\times$10$^{-2}$ mJy/beam" (2.1 ALMA observations)
- time on source: ≈2 hr  
  > "The total on-source exposure time was $\approx$2 hr." (2.1 ALMA observations)
- observing dates: 2011 November 4  
  > "Observations were executed on 2011 November 4" (2.1 ALMA observations)
- pi or archival as stated: Own Cycle 0 Early Science program (PI Kóspál)  
  > "as part of our ALMA Early Science Cycle 0 program" (2.1 ALMA observations)
- Other facility **Herschel PACS/SPIRE**: 70-500 um maps and photometry  
  > "We obtained far-infrared and submillimeter maps of HD 21997" (2.2 Herschel observations)
- Other facility **Spitzer/IRS**: 5.2-38 um spectrum  
  > "covering the $5.2-38\,\mu$m range" (2.3 Spitzer/IRS observation)
- External data: Stellar photosphere model, L=11.3 Lsun  
  > "A stellar photosphere model with a luminosity of 11.3 L$_\odot$ was taken from (cite: moor2011)." (3.3 Modeling of dust distribution) [from (cite: moor2011)]
- External data: SCUBA 850 um flux 8.3±2.3 mJy  
  > "850.00 | 8.3$\pm$2.3 | SCUBA" (Table 1) [from (cite: williams2006)]
- External data: CO gas disk radii (<26 AU, 138±20 AU) and CO mass 0.04-0.08 Mearth  
  > "inner and outer radii of $<$26 AU and 138$\pm$20 AU" (Discussion) [from (cite: kospal2013)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (amplitude scale); J0403-360 bandpass  
  > "Callisto was used to constrain the absolute amplitude scale." (2.1 ALMA observations)
- flux scale uncertainty: 10%  
  > "The uncertainty includes 10% calibration uncertainty." (3.1 ALMA image)
- self calibration: _not stated_

### Imaging

- task: CASA v3.3 CLEAN, MFS  
  > "We performed the imaging with the multi-frequency synthesis (MFS) algorithm with the CASA v3.3" (2.1 ALMA observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum extracted from FDM line-free channels and concatenated with TDM data  
  > "we extracted the continuum emission from the FDM data using line-free channels, and concatenated these with our TDM measurements using appropriate weighting." (2.1 ALMA observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.56x1.26 arcsec, PA -53.4 deg  
  > "a beam size of 1$\ensuremath{''}$56$\times$1$\ensuremath{''}$26" (2.1 ALMA observations)
- final rms: 4.5e-2 mJy/beam  
  > "typical r.m.s noise of 4.5$\times$10$^{-2}$ mJy/beam" (2.1 ALMA observations)

### Inherited from earlier work

- FDM line-observation details and CO analysis  
  > "described in (cite: kospal2013)" (2.1 ALMA observations) [from (cite: kospal2013)]
- IRS spectra binned in 11 bins as before  
  > "the IRS spectra were sampled in 11 adjacent bins using the same method as in (cite: moor2010)" (3.3 Modeling of dust distribution) [from (cite: moor2010)]

### Not stated but needed to reproduce (our reading)

- Line-free channel selection and FDM/TDM weighting
- CLEAN weighting/robust, masks, cell and image size, threshold
- Phase calibrator and flux density of Callisto model
- Model grid ranges and steps for Rin, Rout, p
- Marginal likelihood prior definitions
- Visibility deprojection phase center details
- Whether calibration was by manual script or archive pipeline

## Analysis recipe

1. **Image continuum and measure ring geometry and flux**: Fit ellipse to ring intensity maxima along cuts every 10 deg; derive inclination assuming circular ring; aperture photometry  
  > "These points could be fitted with an ellipse having major and minor axes of 2$\ensuremath{''}$06$\times$1$\ensuremath{''}$73" (3.1 ALMA image)
   - software: CASA
   - parameter: aperture radius 2.8 arcsec centered on star  
  > "circular aperture with a radius of 2$\ensuremath{''}$8 centered on the stellar position" (3.1 ALMA image)
   - assumption: Intrinsically circular ring  
  > "Assuming an intrinsically circular ring, we derived an inclination" (3.1 ALMA image)
   - fitting: _not stated_
   - validation: Compared azimuthal scatter with noise and with emission-free ellipses  
  > "We also defined a number of ellipses of the same size and orientation as the fitted one in different emission-free parts of the map." (3.1 ALMA image)
2. **Herschel photometry and sizes**: Elliptical Gaussian fits with quadratic PSF deconvolution; aperture photometry  
  > "We fitted elliptical Gaussians to the source and PSFs, and used quadratic deconvolution to derive the target’s FWHM sizes" (3.2 Herschel PACS and SPIRE maps)
   - software: HIPE
   - parameter: PACS aperture 20 arcsec, sky annulus 40-50 arcsec  
  > "aperture radius of 20$''$ and sky annulus between 40$''$ and 50$''$" (3.2 Herschel PACS and SPIRE maps)
   - fitting: _not stated_
   - validation: _not stated_
3. **Simple model of ALMA visibilities**: Deproject visibilities, bin radially in 7 klambda, fit with DEBRA optically thin model over grid of Rin, Rout, p and smin  
  > "radially averaged in 7 k$\lambda$ wide bins" (3.3.1 Simple model)
   - software: DEBRA
   - parameter: smax fixed 3000 um; smin 4, 6, 8, 16 um  
  > "The maximum grain size ($s_{max}$) was fixed at 3000$\mu$m" (3.3.1 Simple model)
   - assumption: Silicate (olivine) + amorphous carbon, Mie theory, size exponent -3.5  
  > "The dust size distribution was assumed to be power-law with an exponent of $-$3.5" (3.3.1 Simple model)
   - fitting: Marginal likelihood estimator from chi2 of grid models  
  > "derived using a marginal likelihood estimator, calculated from the $\chi^2$ of the fit of individual models" (3.3.1 Simple model)
   - validation: Model SEDs compared with observations; smin=4 um excluded  
  > "This comparison excluded $s_{min}=4$$\mu$m for its incompatibility with mid-infrared data." (3.3.1 Simple model)
4. **Extended model with cold outer halo**: Simultaneous fit of SED and ALMA visibilities with equal chi2 weight; PACS image consistency check; ALMA flux excluded from SED  
  > "We combined $\chi^2$ values of the SED and ALMA visibilities with equal weight and performed a consistency check on the PACS images." (3.3.2 Extended model)
   - software: DEBRA
   - fitting: Same as simple model  
  > "We used DEBRA with the same modelling setup as above." (3.3.2 Extended model)
   - validation: Convolved models with PACS PSFs compared to images  
  > "the simulated PACS images – calculated by convolving our model them with the appropriately rotated PACS PSFs" (3.3.2 Extended model)

## Software

- **CASA** 3.3: CLEAN imaging  
  > "CASA v3.3 (Common Astronomy Software Applications) task CLEAN" (2.1 ALMA observations)
- **DEBRA** : radiative transfer modelling of visibilities and SED  
  > "The DEBris disk RAdiative transfer code (cite: olofsson2012), developed for optically thin radiation, was used to model the visibilities." (3.3.1 Simple model)
- **HIPE** 9.2: Herschel data reduction  
  > "We reduced the data with HIPE v9.2 using the standard pipeline script." (2.2 Herschel observations)
- **SPICE** 2.5.0: Spitzer IRS extraction  
  > "Spitzer IRS Custom Extraction Software (SPICE v2.5.0)" (2.3 Spitzer/IRS observation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 886 um disk flux | 2.69 | 0.30 | mJy | 1 | obtained 2.69$\pm$0.30 mJy for the total continuum flux of the dust disk |
| Disk inclination (ALMA) | 32.9 | 2.6 | deg | 1 | inclination of 32.9$^\circ$$\pm$2.6$^\circ$ |
| Ring position angle | 21.5 | 3.5 | deg | 1 | a P.A. of 21.5$^\circ$$\pm$3.5$^\circ$ |
| Simple model Rin | 62 | 13 | AU | 3 | $R_{in}=62\pm 13$ AU, $R_{out}=150\pm 47$ AU |
| Simple model Rout | 150 | 47 | AU | 3 | $R_{in}=62\pm 13$ AU, $R_{out}=150\pm 47$ AU |
| Simple model dust mass | 0.09 | 0.03 | Mearth | 3 | $M_{dust}=0.09\pm$0.03 M$_\oplus$ |
| Extended model Rin | 55 | 16 | AU | 4 | $R_{in}=55\pm 16$ AU, $p=-1.6\pm 0.8$ |
| Extended model dust mass | 0.27 | 0.11 | Mearth | 4 | $M_{dust} = 0.27\pm0.11$ M$_\oplus$ |
| Fractional luminosity (extended model) | 4.8e-4 | not stated | dimensionless | 4 | Our extended model gives a fractional luminosity of 4.8$\times$10$^{-4}$ |

## Qualitative findings

- Ring shows no significant azimuthal asymmetry  
  > "there is no observational evidence for any azimuthal asymmetry in the ring." (3.1 ALMA image)
- ALMA flux is ~30% of SCUBA flux, attributed to filtered extended emission  
  > "we suspect that this flux loss occurred because some extended emission was filtered out by the ALMA interferometer." (3.3 Modeling of dust distribution)

## Claim tuples

- H: Is there a dust-poor inner region where gas still exists? | E: Compare dust inner radius from ALMA modelling with CO gas inner radius | R: Rin dust 55±16 AU vs gas <26 AU, 1.8 sigma difference | F: Probably a dust-poor inner hole with co-located gas and dust only between ~55 and ~140 AU | **partially**
- H: Is there a cold extended dust outskirt? | E: Simultaneous fit of SED, PACS profiles and ALMA visibilities | R: Extended model with Rout>490 AU fits long wavelength data | F: Cold extended component exists but is weakly constrained | **partially**
- H: Is the dust in the gaseous disk secondary? | E: Compare grain lifetimes with models of gas-dust interaction | R: Grain lifetime <2e4 yr even with gas-to-dust 100 | F: Dust is secondary, replenished by planetesimals, a hybrid disk | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Self-stirring cannot explain extent beyond ~90 AU; planetary stirring proposed  
  > "The dust disk (and the planetesimal belt) of HD 21997 extends out to $\gg$90AU, which cannot be explained via self-stirring." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Details of grain migration cannot be constrained by the data  
  > "the details of grain migration (e.g. the magnitude of migration) cannot be reliably constrained by the available data" (Discussion)
- Caveat (inferred, ours): Only a compact configuration, so extended emission is filtered and the outer halo is poorly constrained
- Caveat (inferred, ours): Parameter errors are large (p = -2.4±4.5)
- Caveat (inferred, ours): Model grain composition assumed without spectral features

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Model grid definition
- Missing: DEBRA code configuration
- Data volume (inferred): ~10-20 GB (Cycle 0 TDM+FDM)
- Score (inferred): 3/5, Data public in archive and the recipe is described, but imaging and modelling details are sparse.
- Rediscovery candidate: no, Recipe lacks imaging and grid details; the DEBRA modelling is not easily redone.

## Links

- Method: (cite: olofsson2012) (DEBRA radiative transfer code)
- Companion: (cite: kospal2013) (ALMA CO line observations of HD 21997)
- Companion: (cite: moor2011) (Discovery of gas around HD 21997)
- Related: 49 Ceti

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
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
  "facts": 75,
  "stated": 45,
  "rate": 0.6
 },
 "evidence_ok": true
}
```
