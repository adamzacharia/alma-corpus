# Debris Disks in the Scorpius-Centaurus OB Association Resolved by ALMA

`2016ApJ...828...25L` | The Astrophysical Journal 2016 | first author: Lieman-Sifry, Jesse | arXiv: 1606.07068 | DOI: 10.3847/0004-637X/828/1/25

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: debris_disks
- Question: How prevalent is CO gas in ~10 Myr Sco-Cen debris disks, and what are the dust geometry, grain sizes and masses of the resolved disks?  
  > "The sample was selected for large infrared excess and age $\sim$10 Myr, to characterize the prevalence of molecular gas emission in young debris disks." (abstract)
- Target **24 Sco-Cen disks (e.g. HIP 73145, HIP 76310, HIP 84881, HIP 62657, HIP 79516)**: coordinates _not stated_; z/distance 85-151 pc  
  > "Distance to the star from *Hipparcos* parallax measurement (cite: lee07)" (Table of stellar parameters); distance from Hipparcos parallax (van Leeuwen 2007)  
  > "Distance to the star from *Hipparcos* parallax measurement (cite: lee07)" (Table of stellar parameters)

## Data provenance

- ALMA projects: 2012.1.00688.S
- bands: Band 6 (1240 um)  
  > "Band 6 was utilized for all observations, with four dual-polarization spectral windows centered at frequencies of 230.6, 232.6, 245.4, and 247.4 GHz." (2 Observations)
- frequencies and spectral setup: 4 spws at 230.6, 232.6, 245.4, 247.4 GHz; CO spw 234.4 MHz bandwidth, 122.1 kHz channels (0.16 km/s); three 1.875 GHz continuum spws  
  > "has a bandwidth of 234.4 MHz per polarization and a channel spacing of 122.1 KHz (0.16 km s$^{-1}$)." (2 Observations)
- continuum bandwidth: 5.625 GHz per polarization  
  > "were aggregated into a total 5.625 GHz bandwidth (per polarization) for continuum analysis." (2 Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-1284 m projected baselines; 26-36 antennas  
  > "2014 Dec 14 | 6 | 9.73 | 28 | 15-1284" (Table 1)
- angular resolution: 0.5-1 arcsec  
  > "observed at an angular resolution of 0.5$''$-1” with the Atacama Large Millimeter/Submillimeter Array (ALMA)" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 6.88-10.2 min per field  
  > "2014 Mar 23-24 | 5 | 6.88 | 36 | 15-438" (Table 1)
- observing dates: 6 nights, 2013 Dec 14 to 2014 Dec 14 (Cycle 1)  
  > "We obtained ALMA Cycle 1 observations of 24 sources over a total of 6 nights between 2013 Dec 14 and 2014 Dec 14." (2 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.53800 GHz)
- Other facility **Spitzer, IRAS, WISE, AKARI, 2MASS**: Broad-band SED photometry for sample selection and SED fitting  
  > "We cross-matched *Spitzer* and *IRAS* observations with *2MASS*, *WISE*, and *Akari*" (Introduction)
- External data: Stellar effective temperatures and luminosities  
  > "Effective temperatures given by (cite: mcdo12), unless noted." (Table of stellar parameters) [from (cite: mcdo12)]
- External data: Hipparcos distances  
  > "Distance to the star from *Hipparcos* parallax measurement (cite: lee07)" (Table of stellar parameters) [from (cite: lee07)]
- External data: CO-derived inclination and PA for gas-rich disks  
  > "we set best fit values of $i$ and $PA$ from fits to the CO J=2-1 line emission before varying the rest of the disk geometry" (4 Analysis) [from (cite: hal16)]
- External data: Systemic velocities used for CO integration  
  > "All other sources were integrated between $\pm$5 km s$^{-1}$ from their systemic velocities as listed in (cite: kha07)." (Table 3 note) [from (cite: kha07)]

## Processing

### Calibration

- pipeline or manual: CASA reduction scripts from NAASC staff  
  > "CASA reduction scripts for the ALMA data were provided by the staff at the North American ALMA Science Center (NAASC)." (2 Observations)
- casa version: CASA 4.1 or 4.2  
  > "we adopted the Butler-JPL-Horizon 2012 models in CASA version 4.1 or 4.2" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres or Titan (Butler-JPL-Horizons 2012)  
  > "either Ceres or Titan for this sample" (2 Observations)
- flux scale uncertainty: 20% systematic  
  > "is subject to an assumed $20\,\%$ systematic uncertainty" (2 Observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Natural weighting; Briggs robust 0 or 0.5 for resolved sources  
  > "Imaged with a Briggs weighting parameter of 0." (Table 2 notes)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Subtracted using line-free regions of spectrum  
  > "Before imaging the spectral line, the continuum emission was subtracted using the line-free regions of the spectrum." (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Every four channels averaged to 244 kHz  
  > "every four channels in the visibility data were averaged to provide channels with 244 kHz resolution and sampling" (2 Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Disk modeling method and assumptions (visibility+SED, grain temperatures)  
  > "We follow the modeling method and assumptions described in (cite: ric13), the essentials of which we briefly recap below." (4 Analysis) [from (cite: ric13)]
- beta = 0.8  
  > "we set $\beta = 0.8$, a typical value for debris disks modeled using a similar approach (cite: stee15)" (4.2) [from (cite: stee15)]

### Not stated but needed to reproduce (our reading)

- Line-free channels for continuum subtraction
- Exact CASA version per night
- MCMC walkers, steps, burn-in and priors
- SED photometry values used per star
- CO inclination/PA values from Hales et al. (in prep)
- Clean parameters (cell, image size, masks)

## Analysis recipe

1. **Measure continuum flux and resolvedness**: MIRIAD uvfit point source or elliptical Gaussian fits in visibility domain; resolved if major axis >3 sigma  
  > "if the major axis length was measured with a signal-to-noise ratio (SNR) of $> 3\sigma$, we consider the disk spatially resolved" (3.1)
   - software: MIRIAD
   - fitting: _not stated_
   - validation: _not stated_
2. **Visibility-only geometry fits**: Model optically thin disk images (1 AU/pixel) sampled with uvmodel, chi2 compared to visibilities, MCMC for R_In, DeltaR, i, PA  
  > "sample these synthetic images at the same baseline separations and orientations as the data using the MIRIAD task `uvmodel`" (4.1)
   - software: MIRIAD, emcee
   - parameter: surface density power law p = 1 fixed  
  > "we set $p = 1$" (4 Analysis)
   - assumption: i and PA fixed to CO-derived values for gas-rich disks  
  > "we set best fit values of $i$ and $PA$ from fits to the CO J=2-1 line emission" (4.1)
   - fitting: Affine-invariant MCMC (emcee), chi2 likelihood in visibilities  
  > "we utilize the affine-invariant Markov Chain Monte Carlo (MCMC) fitting technique as described by (cite: good10) and implemented in Python as `emcee`" (4.1)
   - validation: Compared with scattered-light geometries  
  > "the values of $PA$ and $i$ that we derive are consistent with the previously determined geometry to within the uncertainties" (4.1)
3. **Simultaneous SED and visibility fit for grain size and mass**: Fix geometry; fit SED (lambda>5 um) plus visibilities with modified blackbody; add unresolved inner belt when needed  
  > "we fix the geometry of the grain population responsible for the continuum emission from the outer disk and then perform simultaneous modeling of the ALMA visibilities and broad-band SED" (4.2)
   - software: emcee
   - parameter: beta = 0.8; rho = 2.7 g cm^-3; grain sizes 0.1-3000 um  
  > "We assume $\rho = 2.7$ g cm$^{-3}$" (4.2)
   - assumption: Compact astrosilicates (Draine 2003), Mie theory temperatures; Kurucz-Lejeune photosphere  
  > "We assume that the composition of the grains is compact astrosilicates (cite: drai03) with characteristic grain size $a$." (4.2)
   - fitting: MCMC; AIC for model comparison  
  > "we find that we need to also vary $a$ in order to successfully recreate the SED and visibilities (raw $\chi^{2}$ in Column ) as justified by the Akaike Information Criterion" (4.2.1)
   - validation: AIC significance of free grain size and inner belt (>10 sigma)  
  > "these models are all significantly better than the models without an inner belt at the $> 10\sigma$ level" (4.2.2)

## Software

- **CASA** 4.1 or 4.2: Calibration of ALMA data  
  > "CASA reduction scripts for the ALMA data were provided by the staff at the North American ALMA Science Center (NAASC)." (2 Observations)
- **MIRIAD** : uvfit flux/size fits and uvmodel  
  > "fitting a point source using the MIRIAD[^2] task `uvfit`" (3.1)
- **emcee** : MCMC fitting  
  > "implemented in Python as `emcee` by (cite: fore13)" (4.1)
- **Astropy** : Python analysis  
  > "Astropy, a community-developed core Python package for Astronomy" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum detections | 20 of 24 | not stated | sources | 1 | A total of 20 of the 24 sources were detected at the $3\sigma$ level by our ALMA observations |
| Spatially resolved disks | 12 | not stated | disks | 1 | of these disks, 12 are spatially resolved by our observations |
| HIP 73145 12CO(2-1) flux | 798 | 35 | mJy beam^-1 km s^-1 | 0 | HIP 73145 / 1.42\times 1.21 / 28 / 10.1 / 16 / 798 $\pm$ 35 / 22.5 |
| HIP 76310 12CO(2-1) flux | 1406 | 78 | mJy beam^-1 km s^-1 | 0 | 1406 $\pm$ 78 |
| HIP 84881 12CO(2-1) flux | 1183 | 37 | mJy beam^-1 km s^-1 | 0 | 1183 $\pm$ 37 |
| HIP 73145 log disk mass | -1.49 | +0.03/-0.03 | log Earth masses | 3 | $-1.49^{+0.03}_{-0.03}$ |

## Qualitative findings

- Gas-rich disks tend to have larger outer radii and smaller grains; no dust-mass difference  
  > "The gas-rich debris disks exhibit preferentially larger outer radii in their dust disks, and a higher prevalence of characteristic grain sizes smaller than the blowout size." (abstract)

## Claim tuples

- H: CO-rich debris disks are common around young intermediate-mass stars | E: CO(2-1) survey of 24 disks | R: Three strong CO debris detections, all A stars, plus two tentative | F: Conditions around A stars favor CO survival or formation | **supported**
- H: Gas-rich disks are larger and have smaller grains | E: Visibility and SED fitting of 12 resolved disks | R: CO-rich disks are three of four largest outer radii; two of three with grains below blowout | F: Suggestive but not conclusive | **partially**
- H: Gas-rich disks have larger dust masses | E: Compared SED+visibility dust masses | R: No correlation | F: Puzzling for second-generation scenario | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: Visibility-domain fitting because noise is well understood and CLEAN images lack well characterized uncertainties  
  > "We carry out this analysis in the visibility domain because the noise is well understood (cite: schw78)" (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Low resolution prevents breaking R_Out/p degeneracy and resolving widths  
  > "we are unable to break the degeneracy between $R_\mathrm{Out}$ and $p$ that arises in our modeling" (4 Analysis)
- Caveat (inferred, ours): Small sample of gas-rich disks
- Caveat (inferred, ours): Fixed p, beta and grain density affect masses and grain sizes
- Caveat (inferred, ours): Hybrid opacity treatment not self-consistent

## Reproducibility

- Data public (paper): Project code given; archival status not explicitly stated  
  > "This work makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00688.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: MCMC settings and priors
- Missing: SED photometry tables
- Missing: CO geometry from Hales et al. in prep
- Missing: Model code from Ricarte et al. 2013 not released here
- Data volume (inferred): ~50-100 GB raw for 5 execution blocks
- Score (inferred): 3/5, Data and recipe mostly described, but fit settings and code are missing.
- Rediscovery candidate: no, Fitting code and MCMC details not provided.

## Links

- Method: Ricarte et al. 2013 (cite: ric13) (Disk modeling method)
- Companion: Hales et al. in prep (cite: hal16) (Detailed CO analysis)
- Related: Sco-Cen debris disk sample

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
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
  "facts": 69,
  "stated": 43,
  "rate": 0.623
 },
 "evidence_ok": true
}
```
