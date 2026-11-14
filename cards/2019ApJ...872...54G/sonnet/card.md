# Orion SrcI’s Disk Is Salty

`2019ApJ...872...54G` | The Astrophysical Journal 2019 | first author: Ginsburg, Adam | arXiv: 1901.04489 | DOI: 10.3847/1538-4357/aafb71

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: Which molecular lines in the Orion SrcI disk spectra are unidentified, are they NaCl/KCl and isotopologues, and how are they excited and produced?  
  > "We report the detection of NaCl, KCl, and their $^{37}$Cl and $^{41}$K isotopologues toward the disk around Orion SrcI." (abstract)
- Target **Orion SrcI**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00165.S
- bands: Band 3 (3.0 mm), Band 6 (1.3 mm), Band 7 (0.87 mm)  
  > "We use the robust 0.5 weighted spectral cubes from all three bands (B3 3.0 mm, B6 1.3 mm, B7 0.87 mm) for our spectroscopic analysis." (2 Observations and Analysis)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.03 arcsec  
  > "a subset of the authors reported 0.03$\arcsec$ ALMA observations of SrcI" (1 Introduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: NaCl v=0-8 rotational lines, e.g. v=1 J=18-17 (not stated)
- Line: KCl v=0-8 rotational lines, e.g. v=0 J=13-12, 45-44 (not stated)
- External data: KCl rest frequencies/catalog (ExoMol line list), corrected here with a bilinear fit  
  > "We obtained the KCl frequencies for these lines from the catalogs of (cite: Barton2014a)" (2 Observations and Analysis) [from (cite: Barton2014a)]
- External data: NaCl frequencies, potential energy and dipole moment functions  
  > "and the NaCl frequencies from (cite: Cabezas2016a), who provided more accurate potential energy and dipole moment functions." (2 Observations and Analysis) [from (cite: Cabezas2016a)]
- External data: NaCl-He collision rates and Fortran code  
  > "(cite: Quintana-Lacaci2016a) calculated collision rates for NaCl with He and provided a Fortran code to compute those rates." (3.2 Excitation) [from (cite: Quintana-Lacaci2016a)]

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
- weighting robust: robust 0.5 cubes  
  > "We use the robust 0.5 weighted spectral cubes from all three bands" (2 Observations and Analysis)
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

- Data, imaging and spectral extraction method  
  > "Appendix D of that paper describes the spectral extraction method, which we summarize here." (2 Observations and Analysis) [from (cite: Ginsburg2018b)]
- Truncated Keplerian disk model of the line emission (inner cutoff 35-40 AU, outer 55-60 AU)  
  > "modeled the line emission now assigned to these salts as a truncated Keplerian disk" (3.1 Spatial distribution) [from (cite: Ginsburg2018b)]

### Not stated but needed to reproduce (our reading)

- Calibration and CASA version and imaging parameters (all in Ginsburg2018b)
- Continuum subtraction and line-free channels
- Distance to Orion adopted
- Pixel region used for stacking and the velocity centroid procedure details
- Gaussian fit initial parameters
- Column densities and RADEX input parameters for the models

## Analysis recipe

1. **Stack spectra**: Find velocity centroid per pixel from NaCl v=1 J=18-17, shift to 0 km/s, average over the region with significant NaCl emission  
  > "We shifted the spectrum along each such pixel to 0 km s$^{-1}$, then averaged the shifted spectra over the region with significant emission in the NaCl line." (2 Observations and Analysis)
   - software: spectral-cube
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify lines**: Match lines with NaCl/KCl catalogs; KCl frequencies corrected with a bilinear fit in v_u and J_u  
  > "We correct for this error by performing a bilinear fit in frequency as a function of $v_u$ and $J_u$." (2 Observations and Analysis)
   - fitting: _not stated_
   - validation: Residual differences generally <0.1 km/s vs other catalogs  
  > "In the transitions available in both catalogs the resulting frequency differences are generally $<0.1$ km s$^{-1}$" (2 Observations and Analysis)
3. **Measure line parameters**: Gaussian fits to detected lines  
  > "We have fit Gaussian line profiles to each of the transitions we flagged as ‘detected’" (2 Observations and Analysis)
   - fitting: _not stated_
   - validation: _not stated_
4. **Excitation analysis**: Rotation and vibration diagrams plus RADEX models with collisional and radiative backgrounds  
  > "we used RADEX (cite: van-der-Tak2007a) to examine the excitation" (3.2 Excitation)
   - software: RADEX, pyradex
   - assumption: H2 collision rates similar to He  
  > "Making the usual assumption that the collision rates with $\textrm{H}_{2}$ are similar to those for He" (3.2 Excitation)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : listed among tools  
  > "and `CASA` (cite: McMullin2007a)" (Software)
- **RADEX/pyradex** : excitation modeling  
  > "We used the `pyradex` wrapper of RADEX for these calculations" (3.2 Excitation)
- **spectral-cube** v0.4.3: cube handling  
  > "`spectral-cube` (cite: Ginsburg2018SpectralCube) and `radio-beam`" (Software)
- **astropy, scipy, numpy, matplotlib, astroquery, radio-beam** : analysis and plotting  
  > "`astropy` (cite: Astropy-Collaboration2013a), `pyradex`" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| KCl v=0 rotational temperature | ~105 | not stated | K | 4 | the best fit is $T_{rot}\sim105$ K |
| 35Cl/37Cl ratio from NaCl | 1.4 | 0.4 | dimensionless | 4 | The ratio $^{35}$/$^{37}$Cl is $r=1.4\pm0.4$. |
| KCl v=0 13-12 peak brightness temperature | 15.3 | 0.9 | K | 3 | $T_{B,max}(\textrm{KCl v=0 13-12}) = 15.3\pm 0.9$ K |
| Vibrational temperatures | 1000 to 5000 | very large | K | 4 | We find values that range from 1000 to 5000 K, although these fits are subject to very large uncertainties. |

## Qualitative findings

- Salt emission traces the region just above the continuum disk, possibly the base of the outflow  
  > "The salt emission traces the region just above the continuum disk, possibly forming the base of the outflow." (abstract)

## Claim tuples

- H: Unidentified lines in SrcI are salts | E: Catalog matching of stacked spectra in three bands | R: About 60 lines of NaCl, KCl and isotopologues detected up to v=6 | F: First ISM detection of these molecules outside evolved-star ejecta | **supported**
- H: Vibrational excitation can be explained by a single temperature in LTE | E: Rotation and vibration diagrams, RADEX models | R: Low rotational but high vibrational temperatures | F: Not LTE; radiative excitation by 25-45 micron field most likely | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: H2 and electron collisions, UV excitation, and dust opacity rejected or disfavored as excitation explanations  
  > "We conclude that there is no simple model that explains the observed pattern of low rotational and high vibrational temperature." (3.2 Excitation)
- How they decided it was enough: _not stated_
- Limitation (authors): Isotopologue ratios uncertain due to excitation uncertainties  
  > "these measurements should be taken with a grain of salt." (Isotopologue abundances)
- Caveat (inferred, ours): Stacking may bias line ratios
- Caveat (inferred, ours): Excitation conclusions rely on a toy radiation field
- Caveat (inferred, ours): Isotope ratios assume optically thin lines

## Reproducibility

- Data public (paper): Code on GitHub and data on Zenodo  
  > "The software used to make this version of the paper is available from github at <https://github.com/keflavich/Orion_ALMA_2016.1.00165.S> with hash 5636c86 (2019-01-01)." (Software)
- Products in archive: _not stated_
- Code: GitHub repository with analysis scripts  
  > "The software used to make this version of the paper is available from github at <https://github.com/keflavich/Orion_ALMA_2016.1.00165.S> with hash 5636c86 (2019-01-01)." (Software)
- Missing: Calibration and imaging details deferred to Ginsburg2018b
- Missing: Stacking region mask
- Data volume (inferred): tens of GB (three-band high-resolution cubes)
- Score (inferred): 3/5, Code released and data public, but processing is inherited from a prior paper and fits are sparsely specified.
- Rediscovery candidate: no, Recipe depends on previous paper's cubes and corrected catalogs; excitation modeling is not fully specified.

## Links

- Method: (cite: Ginsburg2018b) (Observations, imaging and spectral extraction)
- Companion: (cite: Ginsburg2018b) (Earlier analysis of the same data)

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
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
  "facts": 69,
  "stated": 24,
  "rate": 0.348
 },
 "evidence_ok": true
}
```
