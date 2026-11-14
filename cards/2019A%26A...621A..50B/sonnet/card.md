# ALMA observations of the "fresh" carbon-rich AGB star TX Piscium. The discovery of an elliptical detached shell

`2019A&A...621A..50B` | Astronomy and Astrophysics 2019 | first author: Brunner, M. | arXiv: 1811.07577 | DOI: 10.1051/0004-6361/201833652

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: Is the molecular CO(2–1) counterpart of the ring-like dust structure around TX Psc resolved, and what shapes it?  
  > "We investigate the molecular counterpart in high resolution, aiming to resolve the ring-like structure and identify its origin." (abstract)
- Target **TX Psc**: coordinates _not stated_; z/distance 275 (+34/-26) pc  
  > "the most recent distance estimate to the star is $275^{+34}_{-26}$ pc (cite: van-Leeuwen2007)" (Introduction); distance from van Leeuwen 2007  
  > "the most recent distance estimate to the star is $275^{+34}_{-26}$ pc (cite: van-Leeuwen2007)" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00059.S
- bands: _not stated_
- frequencies and spectral setup: CO(2-1) 230.538 GHz at 0.65 km/s resolution; extra windows at 244.936 and 231.221 GHz (CS, 13CS); continuum window at 248.000 GHz  
  > "The spectral setup was optimised for the CO(2–1) line emission at 230.538 GHz with a spectral resolution of 499.84 kHz (0.65 km s$^{-1}$)." (2 Observations)
- continuum bandwidth: 1875 MHz at 248.000 GHz  
  > "one continuum spectral window was set up at 248.000 GHz with a spectral resolution of 0.977 MHz and a bandwidth of 1875 MHz" (2 Observations)
- arrays: Main array (MA), ACA and total power  
  > "consist of main array (MA), Atacama Compact Array (ACA), and total power array data" (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Requested 1"; MA beam 1.06x0.98 arcsec (tapered), ACA 7.60x4.44, TP 28.15  
  > "| MA          | 1.06 $\times$ 0.98   | -80.09     | 5.6                      | 3     |" (Table 2)
- max recoverable scale: MA 5.6", ACA 18.6"  
  > "| ACA         | 7.60 $\times$ 4.44   | -89.26     | 18.6                     | 9     |" (Table 2)
- sensitivity: rms 3 mJy (MA), 9 mJy (ACA), 44 mJy (TP) in line-free channels  
  > "the average rms noise of line-free channels" (Table 2)
- time on source: _not stated_
- observing dates: Cycle 3 (October 2015 – September 2016)  
  > "The ALMA observations were carried out in Cycle 3 (October 2015 – September 2016)" (2 Observations)
- pi or archival as stated: Own proposal, PI M. Brunner  
  > "ALMA Cycle 3 observations (PI: M. Brunner, project ID 2015.1.00059.S)" (Introduction)
- Line: CO J=2-1 (230.538 GHz)
- Other facility **Herschel/PACS**: 70 micron dust emission image for comparison with CO  
  > "thermal dust emission at 70 $\mu$m observed by *Herschel/PACS*" (3.3 Comparison of gas and dust)
- External data: Distance 275 pc  
  > "the most recent distance estimate to the star is $275^{+34}_{-26}$ pc" (Introduction) [from (cite: van-Leeuwen2007)]
- External data: Luminosity 7700 Lsun  
  > "a luminosity $L$ of 7700 L$_{\odot}$ (cite: Claussen1987)" (Introduction) [from (cite: Claussen1987)]
- External data: C/O ratio 1.07  
  > "the average C/O ratio derived from multiple observations and models, as summarised by (cite: Klotz2013), is 1.07" (Introduction) [from (cite: Klotz2013)]
- Simulation/model as data: Stationary dust-driven wind models of rotating polytropes (n=3/2) from Dorfi & Hoefner 1996  
  > "We used the models and estimates of (cite: Dorfi1996) to calculate the effect of stellar rotation in the case of TX Psc." (5 Stellar rotation)

## Processing

### Calibration

- pipeline or manual: Standard calibration in CASA  
  > "Standard calibration of the interferometric data was performed with the Common Astronomy Software Application (CASA)" (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus and Neptune  
  > "using Uranus and Neptune as flux calibrators" (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN, done with Nordic ARC Node  
  > "Imaging of the interferometric data was carried out and improved in collaboration with the Nordic ARC Node[^3] using CLEAN." (2 Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: uv-tapering applied to MA to reach ~1" resolution; untapered image also made  
  > "we used uv-tapering to reduce the angular resolution and gain S/N in the faint regions of the CSE" (2 Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: MA and ACA not combined; analysed separately  
  > "we refrained from combining the MA and ACA data and in the following always analyse the data separately" (2 Observations)
- smoothing: _not stated_
- final beam: Untapered MA beam 0.61x0.57 arcsec  
  > "full resolution of the main array with a beam of 0.61$^{\prime\prime\,}$$\times$ 0.57$^{\prime\prime\,}$" (3.2 Present-day wind)
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CASA version
- tclean/CLEAN parameters (robust, cell, image size, mask, threshold, taper value)
- channel width of imaged cubes
- how total power was combined or imaged
- Shape model fitting criteria (visual comparison only)
- how the spectrum was extracted (aperture)
- dust-driven wind model code and inputs

## Analysis recipe

1. **Measure shell geometry and age**: Measure semi-major/minor axes in channel maps; spectrum gives expansion velocity; age upper limit from radius/velocity  
  > "With an expansion velocity of 10 km/s along the semi-major axis of the shell, the upper limit of the age of the detached shell is $\sim$2600 years." (3.1 Detached shell)
   - parameter: Shell thickness assumed 1"  
  > "we estimate a shell thickness of 1$^{\prime\prime\,}$" (3.1 Detached shell)
   - assumption: Shell extent along line of sight similar to semi-major axis; not significantly tilted  
  > "the ellipsoid is axisymmetric to the semi-minor axis and not significantly tilted with respect to the line of sight" (3.1 Detached shell)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit 3D ellipsoidal model to channel maps**: Render Shape model with elliptical velocity field, vary PA then inclination, compare to channel maps  
  > "we first rendered the 3D model in this configuration with an inclination angle of 90$^\circ$and a position angle (PA) of 0$^\circ$, and subsequently changed first the PA and later the inclination" (3.1 Detached shell)
   - software: Shape
   - parameter: semi-major 22", semi-minor 17", thickness 1"; vmax 10 km/s major axis, 7.7 km/s minor axis  
  > "The corresponding expansion velocity along the semi-minor (polar) axis then equals 7.7 km/s." (3.1 Detached shell)
   - assumption: Homogeneous density, elliptical velocity profile  
  > "created from a geometric model of homogeneous density with attached velocity field" (3.1 Detached shell)
   - fitting: _not stated_
   - validation: Model overlaid on MA and ACA channel maps  
  > "Figure [3](#fig:ACAShape) shows the ACA channel maps overlaid with the best *Shape* model." (3.1 Detached shell)
3. **Model present-day wind**: Same Shape modelling of untapered MA data with measured extents and 5.9 km/s velocity  
  > "The expansion velocity along the semi-major axis is assumed to be the line of sight velocity, 5.9 km/s, as a first approximation, and the expansion velocity along the semi-minor axis is 4.5 km/s." (3.2 Present-day wind)
   - software: Shape
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare gas and dust**: Overlay Herschel 70 micron contours on ACA moment 0 map  
  > "we show an integrated intensity (moment 0) map of the ACA observations overlaid with contours of the *Herschel* observations" (3.3 Comparison of gas and dust)
   - fitting: _not stated_
   - validation: _not stated_
5. **Test stellar rotation as shaping mechanism**: Rotating polytrope (n=3/2) dust-driven wind models of Dorfi & Hoefner; compare axis ratios of density surfaces with observed 1.3; angular momentum J=I*omega  
  > "we approximated these variations along the polar angle by adopting models for slowly rotating polytropes with a polytropic index of $n=3/2$" (5 Stellar rotation)
   - parameter: R* = 325 Rsun; I = 5.2e56 g cm^2  
  > "we obtain a mean stellar radius of $R_\ast = 325\,\hbox{\,R$_{\odot}$\,}$" (5 Stellar rotation)
   - assumption: Uniform rotation of whole convective envelope; distance 275 pc  
  > "we have assumed a uniform rotation of the whole convective envelope" (5 Stellar rotation)
   - fitting: _not stated_
   - validation: Consistent with R* from interferometry (322 Rsun, Cruzalebes 2015)  
  > "which yield a stellar radius of 322  R$_{\odot}$ and a mass of 2  M$_{\odot}$" (5 Stellar rotation)

## Software

- **CASA** : Calibration of interferometric data  
  > "Standard calibration of the interferometric data was performed with the Common Astronomy Software Application (CASA)" (2 Observations)
- **Shape** : 3D geometric modelling and rendering of channel maps  
  > "we constructed a three-dimensional (3D geometrical model with *Shape* (cite: Steffen2011)" (3.1 Detached shell)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Detached shell semi-major axis | ~22 | not stated | arcsec | 1 | extent in the north-west/south-east direction of $\sim$22$^{\prime\prime\,}$(semi-major axis) |
| Detached shell semi-minor axis | ~17 | not stated | arcsec | 1 | only $\sim$17$^{\prime\prime\,}$(semi-minor axis), which results in an axis ratio of 1.3 |
| Shell axis ratio | 1.3 | not stated | dimensionless | 1 | which results in an axis ratio of 1.3 |
| Shell age upper limit | ~2600 | not stated | years | 1 | the upper limit of the age of the detached shell is $\sim$2600 years |
| Best-fit position angle | ~30 (interval 15-45) | not stated | deg | 2 | good fitting PA interval of roughly 15 - 45$^\circ$, with the best fit at a PA of approximately 30$^\circ$ |
| Best-fit inclination | ~100 (interval 90-110) | not stated | deg | 2 | good fitting inclination interval of 90$^\circ$- 110$^\circ$, with the best fit at an inclination of approximately 100$^\circ$ |
| Present-day wind axis ratio | 1.3 (3.25" by 2.5") | high, not quantified | dimensionless | 3 | the axis ratio of the present-day extended emission of 1.3 is the same as for the elliptical shell |
| Rotational velocity explaining ellipticity | ~2 | not stated | km/s | 5 | Model $\sf C$, with a rotational velocity of $\sim 2\,{\rm km/s}$, can explain the observed shell and present-day axis ratio fairly well |
| Moment of inertia of TX Psc | 5.2e56 | not stated | g cm^2 | 5 | we obtain $I_{\rm TX Psc} = 5.2\cdot 10^{56} {\rm g\, cm}^{2}$ |

## Qualitative findings

- CO shell coincides with dust ring; ISM interaction front lies beyond the shell  
  > "The gaseous and dusty emissions seem to coincide very well with each other" (3.3 Comparison of gas and dust)

## Claim tuples

- H: The CO counterpart of the dust ring is a detached shell and is non-spherical | E: ALMA MA/ACA CO(2-1) mapping and Shape modelling | R: Elliptical shell, axes 22" and 17", axis ratio 1.3, inclination ~100 deg | F: First elliptical detached shell discovered | **supported**
- H: Ellipticity is caused by ISM interaction | E: Compare shell with Herschel ISM front and present-day wind shape | R: Front lies beyond the shell; present-day wind has same ellipticity | F: Shaping is internal to the star | **refuted**
- H: Stellar rotation can produce the ellipticity | E: Rotating polytrope wind models and angular momentum estimates | R: v sin i ~2 km/s reproduces axis ratio; brown-dwarf-mass body suffices | F: Engulfed or close brown dwarf could spin up the star | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: MA and ACA analysed separately because primary-beam differences cause artefacts in combination  
  > "Hence, not only is flux lost but also artefacts, which decrease the image quality of a combined image, are introduced." (2 Observations)
- Alternative: ISM interaction and binary companion considered; ISM rejected, binarity not confirmed  
  > "we cannot confidently claim binarity from our observations of the CSE alone" (4.2 Binary companion)
- How they decided it was enough: _not stated_
- Limitation (authors): Shell thickness cannot be reliably constrained due to inhomogeneity  
  > "since it appears to be very inhomogeneous, we cannot reliably constrain it" (3.1 Detached shell)
- Caveat (inferred, ours): Shape fits are visual with no uncertainties
- Caveat (inferred, ours): Geometry assumes axisymmetric ellipsoid and line-of-sight extent equals semi-major axis
- Caveat (inferred, ours): Rotation models are stationary and quasi-spherical, with no temporal information
- Caveat (inferred, ours): Rotation not directly measured

## Reproducibility

- Data public (paper): ALMA project cited in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00059.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Shape model files
- Missing: wind model code
- Data volume (inferred): tens of GB (MA, ACA and TP mosaic)
- Score (inferred): 3/5, Data identified, but imaging parameters are sparse and the model fits are qualitative.
- Rediscovery candidate: no, Imaging recipe is incomplete and main results rely on visual Shape fits and external wind models.

## Links

- Method: Steffen et al. 2011 (cite: Steffen2011) (Shape software)
- Method: Dorfi & Hoefner 1996 (cite: Dorfi1996) (Rotating wind models)
- Companion: Jorissen et al. 2011 (cite: Jorissen2011) (Herschel dust ring and ISM front of TX Psc)
- Related: MESS (Mass loss of Evolved StarS)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
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
  "facts": 74,
  "stated": 42,
  "rate": 0.568
 },
 "evidence_ok": true
}
```
