# Shadows and asymmetries in the T Tauri disk HD 143006: evidence for a misaligned inner disk

`2018A&A...619A.171B` | Astronomy and Astrophysics 2018 | first author: Benisty, M. | arXiv: 1809.01082 | DOI: 10.1051/0004-6361/201833913

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks
- Question: What is the morphology of the HD 143006 disk in scattered light, and do shadows and asymmetries indicate a misaligned inner disk?  
  > "We study the morphology of the disk around the T Tauri star HD 143006, located in the $\sim$5-11 Myr-old Upper Sco region, and we look for signatures of the mechanisms driving its evolution." (abstract)
- Target **HD 143006**: coordinates _not stated_; z/distance 166±4 pc  
  > "It is located at a distance of 166$\pm$4 pc (cite: gaia2018) and belongs to the Upper Sco star-forming region" (Introduction); distance from Gaia DR2 (Gaia Collaboration 2018)  
  > "It is located at a distance of 166$\pm$4 pc (cite: gaia2018) and belongs to the Upper Sco star-forming region" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00395.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesized beam 0.35'' x 0.30'', PA=-73 deg  
  > "HD 143006 was observed by ALMA in Cycle 2 (2013.1.00395.S) with a synthesized beam of 0.35$''$$\times$0.30$''$, PA=-73$^\circ$." (2.2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated)
- Other facility **VLT/SPHERE IRDIS**: J-band polarized scattered light images with and without coronagraph  
  > "HD 143006 was observed with the polarimetric imaging mode of the InfraRed Dual-band Imager and Spectrograph" (2.1 SPHERE imaging)
- Other facility **VLTI/PIONIER**: archival H-band interferometry, inner disk geometry and companion limits  
  > "HD 143006 was observed with the VLTI $H$-band instrument PIONIER" (4.1 Inner disk)
- Other facility **ZIMPOL**: archival optical image from 2015 June 10  
  > "Figure [10](#fig:zim) shows an archival ZIMPOL observation from 2015 June 10." (ZIMPOL optical image)
- External data: 12CO Moment 1 map and continuum data of HD 143006  
  > "we consider the Moment 1 map of the $^{12}$CO line published by (cite: barenfeld2016)" (4.1 Outer disk) [from (cite: barenfeld2016)]
- External data: Dust mass of ~24.3 Earth masses, rescaled to Gaia distance  
  > "(cite: barenfeld2016) derived a dust mass of $\sim$24.3 Earth masses for the disk, by converting the sub-millimeter continuum flux using d=145 pc." (4.2 Hydrodynamic & radiative transfer model) [from (cite: barenfeld2016)]
- External data: Continuum ring model i~30 deg, PA~148 deg  
  > "found i$\sim$30$^\circ$ and PA$\sim$148$^\circ$" (4.1 Outer disk) [from (cite: pinilla2018a)]
- Simulation/model as data: 3D SPH PHANTOM simulation of a disk broken by an inclined equal-mass binary, post-processed with RADMC-3D  
  > "we use 3D hydrodynamical simulations, first presented in (cite: facchini2018)." (4.2 Hydrodynamic & radiative transfer model)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
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

- ALMA data reduction and calibration  
  > "For more details on the data reduction and calibration, we refer the reader to (cite: barenfeld2016), who first presented the data." (2.2 ALMA observations) [from (cite: barenfeld2016)]
- Hydrodynamic simulation setup  
  > "for more details, we refer the reader to (cite: facchini2018)." (4.2 Hydrodynamic & radiative transfer model) [from (cite: facchini2018)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging steps for the CO cube (deferred to Barenfeld et al. 2016)
- How the Moment 1 map was made (clipping, channels) and the noise level for the 2 sigma cut
- Exact MCMC likelihood and convergence criteria
- Whether the data are public in the archive

## Analysis recipe

1. **fit CO Moment 1 map for outer-disk orientation**: Keplerian planar disk velocity map convolved with beam, fit to Moment 1 map with MCMC  
  > "use a simple analytical model of a planar disk in Keplerian rotation around a 1.5 M$_{\odot}$ star." (4.1 Outer disk)
   - software: emcee
   - parameter: 5 free parameters; 1000 steps, 80 walkers; inner radius 2.2 au, outer 250 au  
  > "The chain explores the parameter space with 1000 steps, with 80 walkers." (4.1 Outer disk)
   - assumption: 1.5 Msun star, distance 166 pc, razor-thin disk  
  > "We fix the outer radius of the disk to 250 au and assume a distance of 166 pc." (4.1 Outer disk)
   - fitting: emcee, uniform priors on inclination, PA, systemic velocity, and center offsets; pixels above 2 sigma  
  > "These parameters are sampled with uniform priors in the range of \[0$^\circ$, 90$^\circ$\], \[0$^\circ$, 360$^\circ$\]" (4.1 Outer disk)
   - validation: Compared with continuum-based estimate; thin-disk approximation judged reasonable at low inclination  
  > "considering the rather low inclination of the system, it is a reasonable approximation." (4.1 Outer disk)

## Software

- **emcee** : MCMC fit of CO velocity map  
  > "We perform our fit with the Markov chain Monte Carlo (MCMC) method using `emcee`" (4.1 Outer disk)
- **RADMC-3D** : 3D radiative transfer of SPH snapshot  
  > "use the 3D radiative transfer code RADMC-3D" (4.2 Hydrodynamic & radiative transfer model)
- **PHANTOM** : SPH hydrodynamic simulation  
  > "performed with the Smoothed Particle Hydrodynamics (SPH) code PHANTOM" (4.2 Hydrodynamic & radiative transfer model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Outer disk inclination from 12CO | 17.5 | 0.2 | deg | 1 | i=17.5$^\circ$$\pm$0.2$^\circ$ and PA=169.8$^\circ$$\pm$0.5$^\circ$ |
| Outer disk PA from 12CO | 169.8 | 0.5 | deg | 1 | i=17.5$^\circ$$\pm$0.2$^\circ$ and PA=169.8$^\circ$$\pm$0.5$^\circ$ |

## Qualitative findings

- Scattered light shows two rings, two gaps, east/west asymmetry, two shadows and an overbrightness at PA 110-170 deg  
  > "Our observations reveal two rings and two gaps, a strong east/west brightness asymmetry, an overbrightness along a narrow range of position angles (110-170$^\circ$), and two dark narrow lanes." (Conclusions)

## Claim tuples

- H: Shadows and asymmetry arise from a misaligned inner disk | E: Compared SPHERE image to SPH plus RADMC-3D warped-disk model with ~30 deg misalignment | R: Model reproduces the east/west asymmetry and shadows but not the PA~140 deg overbrightness | F: A moderately misaligned inner disk is likely | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Inclined magnetic field warp disfavored by ZIMPOL comparison; Kozai scenario deemed implausible  
  > "although our marginal evidence that the shadows have not rotated within a year does not support the latter scenario." (Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Equal-mass binary in model is excluded by detection limits; model temperature not self-consistent  
  > "We note that the temperature profiles of the hydrodynamical and radiative transfer simulations are not computed self-consistently." (4.2 Hydrodynamic & radiative transfer model)
- Caveat (inferred, ours): ALMA used only as a Moment 1 map for geometry
- Caveat (inferred, ours): Thin-disk model ignores flaring
- Caveat (inferred, ours): Model match is qualitative

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Moment 1 map unless regenerated from archive
- Missing: SPH snapshot and RADMC-3D inputs
- Data volume (inferred): ~10 GB for the ALMA CO cube
- Score (inferred): 3/5, ALMA part is a small, well-defined MCMC fit, but the main results rely on SPHERE data and simulations.
- Rediscovery candidate: no, The main results come from SPHERE and simulations, not from public ALMA data.

## Links

- Method: (cite: facchini2018) (Source of the hydrodynamic simulations)
- Companion: (cite: barenfeld2016) (First presentation of the ALMA data)

## Checks

```json
{
 "quotes": 30,
 "quotes_ok": 30,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00526.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 24,
  "rate": 0.381
 },
 "evidence_ok": true
}
```
