# The Proper Motions of the Double Radio Source n in the Orion BN/KL Region

`2017ApJ...834..140R` | The Astrophysical Journal 2017 | first author: Rodríguez, Luis F. | arXiv: 1612.00107 | DOI: 10.3847/1538-4357/834/2/140

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation
- Question: Do BN, I and the double source n move away from a common origin about 500 years ago, and when was the closest approach of BN and I?  
  > "We confirm that all three sources are moving away at transverse velocities of tens of km s$^{-1}$ from a region in-between them, where they were located about 500 years ago." (abstract)
- Target **Orion BN/KL sources BN, I and n**: coordinates BN: 05h35m14.110s, -05d22m22.67s (J2000, epoch 2012.76)  
  > "At a distance of 414 pc (Menten et al. 2007, see however a new estimate of 388 pc by Kounkel et al. 2016)" (Individual Proper Motions); z/distance 414 pc  
  > "At a distance of 414 pc (Menten et al. 2007, see however a new estimate of 388 pc by Kounkel et al. 2016)" (Individual Proper Motions); distance from Menten et al. 2007  
  > "At a distance of 414 pc (Menten et al. 2007, see however a new estimate of 388 pc by Kounkel et al. 2016)" (Individual Proper Motions)

## Data provenance

- ALMA projects: 2012.1.00123.S
- bands: ALMA epoch at 0.09 cm wavelength (the VLA data span 0.7–6 cm)  
  > "2014 Jul 14 (2014.57)$^{d}$ | 2012.1.00123.S | 0.09" (Table 3)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ALMA synthesized beam 0.25"x0.18", PA +66 deg  
  > "$0\rlap.{''}25\times0\rlap.{''}18; +66^\circ$" (Table 3)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2014 Jul 14 (2014.57) for the ALMA epoch  
  > "2014 Jul 14 (2014.57)$^{d}$" (Table 3)
- pi or archival as stated: _not stated_
- Other facility **VLA / Jansky VLA (archival)**: Main astrometric epochs, 1985–2014, mostly in A configuration, used for proper motions  
  > "In particular, all are made in the highest angular resolution A configuration." (Observations)
- External data: Mean proper motion of the Trapezium-BN/KL region used to correct to the Orion rest frame  
  > "as determined by Dzib et al. (2016)" (Testing the Plasma Ejection Scenario) [from Dzib et al. 2016 (cite: D16)]
- External data: 7.3 and 4.7 GHz flux densities of source n used for spectral indices  
  > "Using the data of Forbrich et al. (2016) we obtain a total flux density of 1.45$\pm$0.03 mJy at 7.3 GHz" (Testing the Plasma Ejection Scenario) [from Forbrich et al. 2016 (cite: 2016ApJ...822...93F)]
- External data: 14 relative-position data points of BN and I  
  > "23 data points (14 from Gómez et al. 2008 and 9 from this paper)" (The Minimum Separation of BN and source I in the past) [from Gómez et al. 2008 (cite: 2008ApJ...685..333G)]

## Processing

### Calibration

- pipeline or manual: NRAO Jansky VLA pipeline for the calibration of the JVLA data  
  > "In the calibration stage we used the pipeline provided for Jansky VLA observations by NRAO." (Observations)
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

- Detailed analysis of a subset of the data  
  > "The detailed analysis of a subset of the data is presented in Gómez et al. (2008)." (Observations) [from Gómez et al. 2008 (cite: 2008ApJ...685..333G)]
- Formalism for the minimum separation and its epoch  
  > "Following Gómez et al. (2008) we define as $x(t)$ and $y(t)$ the separations in right ascension and declination of BN with respect to source I" (The Minimum Separation of BN and source I in the past) [from Gómez et al. 2008 (cite: 2008ApJ...685..333G)]

### Not stated but needed to reproduce (our reading)

- How the ALMA data were calibrated and imaged, and how the BN and I positions were measured (fitting method)
- ALMA band, frequency setup and array configuration
- Which gain calibrators were used in each epoch
- Fitting code for the proper-motion least-squares fits

## Analysis recipe

1. **Measure source positions at each epoch**: Calibrate VLA/JVLA data and produce images in AIPS to derive positions  
  > "The final analysis and production of contour images was all made within the older but more mature AIPS software." (Observations)
   - software: AIPS, CASA
   - fitting: _not stated_
   - validation: Systematic errors of about 0.01 arcsec added in quadrature to obtain a reduced chi2 of 1  
  > "adding in quadrature systematic errors of order $\sim0\rlap.{''}01$ to the formal position uncertainties to obtain a reduced $\chi^2$ = 1" (Observations)
2. **Fit the relative BN–I motion and derive the closest approach**: Least-squares fit to 23 relative positions; t_min and s_min from the analytic formulae with standard error propagation  
  > "The least squares fit to 23 data points (14 from Gómez et al. 2008 and 9 from this paper)" (The Minimum Separation of BN and source I in the past)
   - assumption: Distance 414 pc  
  > "At a distance of 414 pc this corresponds to a physical separation of $\sim$120 AU." (The Minimum Separation of BN and source I in the past)
   - fitting: Least squares  
  > "The least squares fit to 23 data points (14 from Gómez et al. 2008 and 9 from this paper) from the VLA, Jansky VLA and ALMA archives" (The Minimum Separation of BN and source I in the past)
   - validation: Agreement with Gómez et al. 2008 within 1–2 sigma  
  > "The proper motions for source BN and I coincide within about $\pm1$–$\sigma$ to $\pm2$–$\sigma$ with those of Gómez et al. (2008)." (Observations)

## Software

- **AIPS** : Analysis of VLA data and production of contour images  
  > "The final analysis and production of contour images was all made within the older but more mature AIPS software." (Observations)
- **CASA** : Jansky VLA data calibration  
  > "the latter one for the Jansky VLA observations" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Epoch of closest BN–I separation | 1475 | ±6 | yr | 2 | $$t_{min} = 1475 \pm 6,$$ |
| Minimum BN–I separation | 0.007 | ±0.093 | arcsec | 2 | $$s_{min} = 0\rlap.{''}007 \pm 0\rlap.{''}093,$$ |
| BN proper motion in RA | -7.0 | ±0.4 | mas/yr | 1 | –7.0$\pm$0.4 |
| Spectral index of source n | -0.3 | ±0.1 | dimensionless | 0 | This gives a spectral index of -0.3$\pm$0.1 |

## Qualitative findings

- Source n shows a new southern component interpreted as one-sided ejected free-free plasma after 2006.36  
  > "Source n exhibits a new component that we interpret as due to a one-sided ejection of free-free emitting plasma that took place after 2006.36." (abstract)

## Claim tuples

- H: BN, I and n recede from a common origin about 500 years ago | E: Proper motions from VLA/JVLA epochs 1991–2014 | R: The extrapolated positions overlap in the past, and the data are consistent with a disintegration epoch in the XVth century | F: A common origin is confirmed, including for source n | **supported**
- H: BN and I had a close encounter | E: Relative astrometry with 23 points including one ALMA point | R: t_min = 1475±6 | F: They were within about 120 AU in the past | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Combining different configurations, frequencies and telescopes can affect the results  
  > "can affect the results" (The Minimum Separation of BN and source I in the past)
- Caveat (inferred, ours): Only one ALMA point is used, so the ALMA contribution is minor
- Caveat (inferred, ours): Uncertainty in the distance (414 vs 388 pc) affects physical scales

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA position measurement details
- Missing: Epoch-by-epoch position fits
- Data volume (inferred): Hundreds of GB (many archival VLA epochs plus one ALMA dataset)
- Score (inferred): 3/5, Archival data are named but the processing is sparsely described.
- Rediscovery candidate: no, ALMA plays a minor role and the processing is incompletely specified.

## Links

- Method: Gómez et al. 2008 (Earlier proper-motion analysis and formalism)
- Companion: Goddi et al. 2011 (Independent proper-motion study)

## Checks

```json
{
 "quotes": 33,
 "quotes_ok": 33,
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
  "facts": 60,
  "stated": 24,
  "rate": 0.4
 },
 "evidence_ok": true
}
```
