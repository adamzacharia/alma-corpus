# Molecular Clouds resolved with ALMA ^{12}CO J=1-0 and J=2-1 observations towards the Magellanic Bridge

`2019BAAA...61..134V` | Boletin de la Asociacion Argentina de Astronomia La Plata Argentina 2019 | first author: Valdivia, M. T. | arXiv: - | DOI: -

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, nearby_galaxies
- Question: Can ALMA resolve individual molecular clouds in Magellanic Bridge regions B and C, and do their properties follow the trends of other metal-poor Local Group clouds?  
  > "We compare the molecular clouds in this metal-poor region with others found in metal-poor galaxies of the Local Group and in the Milky" (1. Introduction)
- Target **MagBridgeB**: coordinates _not stated_; z/distance 63 kpc (assumed same as SMC)  
  > "we assume that the Magellanic Bridge is at a similar distance from us as the SMC (63 kpc away, Harries et al. 2003)" (2. Data); distance from Harries et al. 2003  
  > "we assume that the Magellanic Bridge is at a similar distance from us as the SMC (63 kpc away, Harries et al. 2003)" (2. Data)
- Target **MagBridgeC**: coordinates _not stated_; z/distance 63 kpc (assumed same as SMC)  
  > "we assume that the Magellanic Bridge is at a similar distance from us as the SMC (63 kpc away, Harries et al. 2003)" (2. Data); distance from Harries et al. 2003  
  > "we assume that the Magellanic Bridge is at a similar distance from us as the SMC (63 kpc away, Harries et al. 2003)" (2. Data)

## Data provenance

- ALMA projects: 2015.1.01013.S
- bands: Band 3 (J=1-0), Band 6 (J=2-1)  
  > "the J = 1 − 0 line cube was carried out in band 3 using the main array 12m antennas" (2. Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m main array (1-0); ACA 7m (2-1)  
  > "in band 6 using the Atacama Compact Array (ACA) 7 m antennas at a rest frequency of 230.8 GHz." (2. Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Beams 3.3x2.5 (B, 1-0), 6.9x6.0 (B, 2-1), 3.6x3.3 (C, 1-0), 6.6x5.7 arcsec (C, 2-1)  
  > "Beam major [′′] 3.3 6.9 3.6 6.6" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (115.2 GHz)
- Line: 12CO J=2-1 (230.8 GHz)
- External data: Comparison cloud data for dwarf galaxies (size-linewidth and mass-luminosity)  
  > "We plot data from Bolatto et al. (2008), Wong et al. (2011), Rubio et al. (2015) and Schruba et al. (2017)" (3.2 Physical properties) [from Bolatto et al. 2008; Wong et al. 2011; Rubio et al. 2015; Schruba et al. 2017]
- External data: Galactic plane cloud relations: Larson exponent 0.5, mass-luminosity 0.81  
  > "which have a power law exponent α of 0.5 for Larson’s law and 0.81 for mass vs. luminosity (Solomon et al., 1987)" (3.2 Physical properties) [from Solomon et al., 1987]

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
- smoothing: 1-0 cube and integrated image convolved to the 2-1 beam for line ratios  
  > "we convolved the J = 1 − 0 integrated image and line cube to the same resolution of the corresponding J = 2 − 1 map for each source" (2. Data)
- final beam: See Table 1 beams  
  > "Beam minor [′′] 2.5 6.0 3.3 5.7" (Table 1)
- final rms: Integrated rms 0.11, 1.23 (B), 0.23, 1.26 (C) Jy/beam km/s  
  > "rms [Jy beam−1 km s−1 ] 0.11 1.23 0.23 1.26" (Table 1)

### Inherited from earlier work

- Virial mass from equation 3 with k2=190 for rho ∝ r^-1  
  > "The virial mass Mvir was calculated using equation 3 of MacLaren et al. (1988)" (3.2 Physical properties) [from MacLaren et al. (1988)]
- CO luminosity formula  
  > "is the luminosity distance in Mpc (Bolatto et al., 2013)" (3.2 Physical properties) [from Bolatto et al., 2013]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging details (tclean parameters, weighting, robust)
- How 12m and ACA data were reduced or combined; whether pipeline products used
- Continuum subtraction and line-free channels
- Cloud-by-cloud measured values (only ranges given)
- Priors, likelihood and sampler setup for the MCMC fit
- How FWHM to velocity dispersion conversion was done
- Mask/cutoff for the peak temperature measurement
- Coordinates of targets

## Analysis recipe

1. **Identify clouds**: Integrate cubes over velocity range, take rms, set 3σ contours on J=1-0 moment map to define each cloud area  
  > "using a contour map set at 3 σ over the image, the area covered by each cloud was determined." (2. Data)
   - software: CASA
   - parameter: Velocity integration 140-149 km/s (B), 175-182 km/s (C)  
  > "integrated through the velocity axis between 140 and 149 km s −1 for MagBridgeB and 175 and 182 km s −1 for MagBridgeC" (2. Data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract mean spectra and line parameters**: Mean spectrum per cloud within contours to estimate center, peak temperature and FWHM  
  > "we obtained the mean spectra of each source with casa, which we used to estimate the center, peak temperature, and FWHM of each cloud." (2. Data)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive physical properties**: Req from projected area; Mvir; LCO = 2453 S dV D_L^2; Mmol with alpha_CO  
  > "We have derived the radii, luminosities and virial and H 2 masses for each of the clouds based on the J = 1 − 0 line cube." (3.2 Physical properties)
   - parameter: k2 = 190  
  > "we used a value of k 2 = 190 for a density distribution of ρ ( r ) ∝ r −1" (3.2 Physical properties)
   - assumption: Spherical clouds; distance 63 kpc; alpha_CO = 4.3 Msun (K km/s pc2)^-1 (XCO = 1e20)  
  > "galactic H 2 mass to CO luminosity factor α CO = 4.3 M ⊙ (K km s −1 pc 2 )" (3.2 Physical properties)
   - fitting: _not stated_
   - validation: _not stated_
4. **Line ratios**: Ratio of peak temperatures T(2-1)/T(1-0) after convolving 1-0 to 2-1 resolution and using 2-1 3σ contours  
  > "We define the line ratio as the ratio between the peak temperature of the spectra, in Kelvin, for both transitions" (3.3 Line Ratios)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit scaling relations**: Power-law fit to all dwarf-galaxy clouds for size-linewidth and Mvir-LCO  
  > "Using Maximum Likelihood and Markov Chain Monte Carlo (MCMC), we fit the best line that correlates them all." (3.2 Physical properties)
   - fitting: Maximum likelihood and MCMC; details not stated  
  > "Using Maximum Likelihood and Markov Chain Monte Carlo (MCMC), we fit the best line that correlates them all." (3.2 Physical properties)
   - validation: Compared with indices from Solomon et al. 1987 and Rubio et al. 2015  
  > "similar to the indexes (0.5 and 0.52) found by Solomon et al. (1987) and Rubio et al. (2015) respectively" (3.2 Physical properties)

## Software

- **CASA** : Reduction, cleaning, mean spectra extraction  
  > "The reduction and cleaning of the data was done using Common Astronomy Software Applications (casa)." (2. Data)
- **APLpy** : Plotting  
  > "APLpy, an open-source plotting package for Python (Robitaille and Bressert, 2012)" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of clouds in B | 5 | not stated | dimensionless | 1 | we detected 5 molecular features for source B (labeled from 1 to 5) and 7 for source C |
| Number of clouds in C | 7 | not stated | dimensionless | 1 | we detected 5 molecular features for source B (labeled from 1 to 5) and 7 for source C |
| Req range B | 1.9-4.5 | not stated | pc | 3 | B 0.3 - 0.8 1.9 - 4.5 349 - 2578 3.7 - 106.0 16 - 456 0.82 - 1.36 |
| Req range C | 0.5-2.5 | not stated | pc | 3 | C 0.3 - 0.7 0.5 - 2.5 91 - 984 3.9 - 137.7 17 - 592 0.86 - 1.96 |
| Line ratio range | 0.8-1.4 (abstract); Table: 0.82-1.96 | not stated | dimensionless | 4 | the line ratios are all close to 1 (ranging from 0.8 to 1.4) |
| Larson law index | 0.41 | not stated | dimensionless | 5 | A power law fit gave us an exponential index of 0.41 for Larson’s law |
| Mvir vs LCO index | 0.66 | not stated | dimensionless | 5 | and of 0.66 for virial mass vs. luminosity, lower than the index for galactic plane clouds. |

## Qualitative findings

- Virial mass at least 5 times greater than molecular mass from Galactic alpha_CO, implying higher conversion factor at low metallicity  
  > "There is a tendency for the virial mass to be at least 5 times greater than the molecular mass, calculated using the galactic value." (3.2 Physical properties)

## Claim tuples

- H: ALMA resolves individual clouds in MagBridge B and C | E: 3σ contours on CO(1-0) integrated maps | R: 5 clouds in B, 7 in C | F: Previous detections resolve into 12 clouds, radii <5 pc | **supported**
- H: Clouds follow trends of other metal-poor clouds | E: Compared Req-sigma and Mvir-LCO with literature and fit power laws | R: Indices 0.41 and 0.66 | F: Clouds follow same trends, approximate virial equilibrium | **supported**
- H: Gas is cold and optically thick | E: Line widths and 2-1/1-0 ratio | R: Δv narrow, ratios near 1 | F: Cold, quiescent, optically thick gas | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Procedure cannot separate clouds that differ only in velocity, only spatially resolved ones  
  > "not recognize clouds that have a different structure in the velocity axis, but only separates clouds if they can be spatially resolved." (2. Data)
- Caveat (inferred, ours): Distance assumed equal to SMC; Bridge depth uncertain
- Caveat (inferred, ours): Linewidth in abstract (0.7-1.8) differs from Table 2 (0.3-0.8)
- Caveat (inferred, ours): Line ratio range differs between abstract and Table 2
- Caveat (inferred, ours): Fit of mixed samples with no stated uncertainties

## Reproducibility

- Data public (paper): ALMA project cited; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01013.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Per-cloud tables
- Missing: MCMC details
- Missing: Literature cloud data compilation
- Data volume (inferred): ~20-50 GB (Band 3 12m plus Band 6 ACA, two fields)
- Score (inferred): 3/5, Public data and simple recipe, but imaging and fitting details missing; short proceedings paper.
- Rediscovery candidate: no, Imaging and fitting settings and per-cloud values are not given.

## Links

- Method: MacLaren et al. (1988) (Virial mass formula)
- Method: Bolatto et al., 2013 (CO luminosity and alpha_CO)
- Companion: Rubio et al., 2015 (Metal-poor dwarf galaxy cloud comparison sample)

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 30,
  "rate": 0.417
 },
 "evidence_ok": true
}
```
