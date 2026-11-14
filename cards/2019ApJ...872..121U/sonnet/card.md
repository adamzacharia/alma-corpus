# Molecular Cloud Cores in the Galactic Center 50 km s<SUP>-1</SUP> Molecular Cloud

`2019ApJ...872..121U` | The Astrophysical Journal 2019 | first author: Uehara, Kenta | arXiv: 1903.01759 | DOI: 10.3847/1538-4357/aafee7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, star_formation
- Question: Does cloud-cloud collision in the Galactic Center 50 km/s molecular cloud compress gas and form massive bound cores, and how does the core mass function compare with Orion A?  
  > "The distributions indicate that the CCC compresses the molecular gas and increases the number of the dense bound cores." (abstract)
- Target **Galactic Center 50 km/s Molecular Cloud (G-0.02-0.07)**: coordinates (l, b) = (-0.018, -0.072) as printed  
  > "corresponding to 0 . 083 pc × 0 . 058 pc at the distance to the Galactic Center (8 . 5 kpc)" (2. OBSERVATION); z/distance 8.5 kpc  
  > "corresponding to 0 . 083 pc × 0 . 058 pc at the distance to the Galactic Center (8 . 5 kpc)" (2. OBSERVATION); distance from assumed distance to the Galactic Center  
  > "corresponding to 0 . 083 pc × 0 . 058 pc at the distance to the Galactic Center (8 . 5 kpc)" (2. OBSERVATION)

## Data provenance

- ALMA projects: 2012.1.00080.S
- bands: _not stated_
- frequencies and spectral setup: 4 SPWs centered at 97.987, 96.655, 86.910, 85.723 GHz; 937.5 MHz bandwidth, 244.141 kHz channels  
  > "The center frequencies of the spectral window (SPW) 0, 1, 2 and 3 are 97.987, 96.655, 86.910 and 85.723 GHz, respectively." (2. OBSERVATION); "The bandwidth and frequency resolution of each SPW are 937.5 MHz and 244.141 kHz/1ch, respectively." (2. OBSERVATION)
- continuum bandwidth: _not stated_
- arrays: 12m array, ACA, Total Power  
  > "using the 12m array, Atacama Compact Array (ACA) and Total Power telescope (TP)" (2. OBSERVATION)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: H13CO+: 2.04x1.41 arcsec; C34S: 2.00x1.35 arcsec  
  > "Angular resolution [arcsec 2 ] 2 . 04 × 1 . 41 2 . 00 × 1 . 35" (Table 1)
- max recoverable scale: ACA resolved-out scale ~80 arcsec  
  > "the resolved-out scale of the ACA is ∼ 80 ′′" (2. OBSERVATION)
- sensitivity: rms 0.16 K per 2 km/s channel  
  > "The rms noise levels of the H 13 CO + J = 1 − 0 and C 34 S J = 2 − 1 channel maps are σ rms = 0 . 16 K in brightness temperature." (2. OBSERVATION)
- time on source: _not stated_
- observing dates: May 31, 2013 to Jan 23, 2015  
  > "on May 31, 2013 to Jan 23, 2015" (2. OBSERVATION)
- pi or archival as stated: Cycle 1 program, PI M. Tsuboi  
  > "(2012.1.00080.S,PI M.Tsuboi)" (2. OBSERVATION)
- Line: H13CO+ J=1-0 (86.754 GHz)
- Line: C34S J=2-1 (96.413 GHz)
- Other facility **NRO45**: Single-dish map used for comparison of flux recovery; C32S J=2-1 from ACA+TP; SiO/H13CO+ ratio earlier  
  > "Figure 2 shows the spectra of the ALMA feathering map, the ALMA interferometer map, and the NRO45 map." (3. CHANNEL MAPS)
- Other facility **NMA**: C32S J=1-0 data used for LVG excitation temperature  
  > "from the C 32 S J = 1 − 0 (NMA: Tsuboi et al. 2009) and 2 − 1 (our ACA+TP data) emission line data" (4.2. Mass estimation)
- External data: H13CO+ fractional abundance 6e-11 (factor 2) and C34S 4.87e-10  
  > "The X (H 13 CO + ) is assumed to be 6 × 10 − 11 with uncertainty of a factor of 2 in the CMZ (Amo-Baladr´on et al. 2011)." (4.2. Mass estimation) [from Amo-Baladrón et al. 2011]
- External data: Orion A core catalog/CMF (H13CO+) for comparison  
  > "observed by the H 13 CO + J = 1 − 0 emission line (Ikeda et al. 2007)" (5.3. Comparison) [from Ikeda et al. 2007]
- External data: 44 GHz class I methanol maser positions  
  > "the positions of the 44GHz class I methanol maser (McEwen et al. 2016)" (5.4.1. The CCC in the 50MC) [from McEwen et al. 2016]

## Processing

### Calibration

- pipeline or manual: 12m and TP manual script; ACA pipeline script, in CASA  
  > "The obtained data of the 12m array and TP were reduced using the manual script and those of the ACA were reduced using the pipeline script in the CASA software" (2. OBSERVATION)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: concat of 12m+ACA in uv-plane; clean; feathering with TP  
  > "The data of the 12m array and ACA were concatenated with the task ”concat” in the uv-plane." (2. OBSERVATION)
- deconvolver: _not stated_
- weighting robust: briggs, robust = 0.5  
  > "using the ”briggs” weighting with a robust parameter of 0.5 in the ”clean” of the CASA" (2. OBSERVATION)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: interferometer and TP maps combined by feathering  
  > "The interferometer maps and the TP maps were combined with the task ”feathering”" (2. OBSERVATION)
- smoothing: velocity resolution 2 km/s (from original ~0.75 km/s)  
  > "the velocity resolutions of the created maps are 2 km s − 1 for improving the noise level" (2. OBSERVATION)
- final beam: 2.04x1.41 arcsec PA -39.40 deg (H13CO+); 2.00x1.35 PA -30.3 (C34S)  
  > "The angular resolution of the H 13 CO + J = 1 − 0 map is 2 ′′ . 04 × 1 ′′ . 41 at PA = − 39 . 40 ◦" (2. OBSERVATION)
- final rms: 0.16 K  
  > "σ rms = 0 . 16 K in brightness temperature" (2. OBSERVATION)

### Inherited from earlier work

- clumpfind core identification and deconvolution formulae  
  > "using the clumpfind algorithm (Williams et al. 1994)" (4.1.) [from Williams et al. 1994 (cite: Williams et al. 1994)]
- CCC interpretation and shock tracer R_T from earlier NRO45 work  
  > "Tsuboi et al. (2015) found the half-shell-like shock structure" (5.4.1.) [from Tsuboi et al. 2015]

### Not stated but needed to reproduce (our reading)

- CASA version
- clean mask, threshold, multiscale and cell/image size
- line-free channels / continuum subtraction
- Flux calibrator and flux scale uncertainty
- Feathering scale factor / TP calibration
- Clumpfind details such as how Tex per core was assigned from LVG grid
- Fitting method and binning for CMF power law
- Definition of CCC region mask beyond R_T>2.5

## Analysis recipe

1. **Image and combine data**: concat 12m+ACA, clean with briggs, feather with TP; 2 km/s channels  
  > "The interferometer maps and the TP maps were combined with the task ”feathering”" (2. OBSERVATION)
   - software: CASA
   - parameter: robust = 0.5  
  > "robust parameter of 0.5" (2. OBSERVATION)
   - fitting: _not stated_
   - validation: flux ratio to NRO45: interferometer ~0.15, feathered ~0.8  
  > "The flux density ratio of the ALMA interferometer map to the NRO45 map is ∼ 0 . 15, whereas the ratio of the ALMA feathering map to the NRO45 map is as high as ∼ 0 . 8." (3. CHANNEL MAPS)
2. **Identify core candidates**: clumpfind in 3D l-b-v cube 0-100 km/s, maps resampled to 1.5 arcsec; reject small/unresolved candidates  
  > "Lowest contour level and Contour increment, were set to 2 σ and 2 σ corresponding to 0.32 K and 0.32 K, respectively." (4.1.)
   - software: clumpfind
   - parameter: contour level and increment 2σ = 0.32 K; reject R<0.035 pc, <3 pixels at ≥3σ or <2 channels  
  > "we rejected the detected core candidates that do not have three or more pixels with intensities of ≥ 3 σ or the core candidates that do not have two or more velocity channels" (4.1.)
   - fitting: _not stated_
   - validation: _not stated_
3. **Estimate Tex, column density, LTE and virial masses**: RADEX LVG on C32S 1-0 and 2-1 for Tex per core; LTE N(H2) from line intensities; mass sums; virial mass 210 R dV^2; alpha = Mvir/MLTE  
  > "we used the T ex obtained for each core candidate in the column density estimation" (4.2. Mass estimation)
   - software: RADEX
   - assumption: X(H13CO+)=6e-11, X(C34S)=4.87e-10, distance 8.5 kpc, mu=2.35e-57 Msun, no external pressure or magnetic field  
  > "We estimate the virial masses of the core candidates assuming no external pressure and no magnetic field." (4.2. Mass estimation)
   - fitting: _not stated_
   - validation: C34S abundance compared to Orion A estimate  
  > "This value is consistent with that in the 50MC." (4.2. Mass estimation)
4. **Select bound cores and compare CCC vs non-CCC**: bound if alpha<2; CCC region defined as R_T=TB(SiO 2-1)/TB(H13CO+ 1-0)>2.5; compare CDFs and densities  
  > "we define the region with the high brightness temperature ratio, R T > 2 . 5, as the CCC region because this region can cover the maser distribution" (5.4.1.)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit core mass function**: single power law dN/dM ∝ M^-alpha above mass thresholds, chi2 reported  
  > "by using a usual single power-law function given by" (5.3.)
   - parameter: mass ranges >450 Msun (H13CO+ whole), >600 (CCC), >200 (non-CCC); C34S 600-2000 Msun  
  > "We applied a single power-law function to the CMF of the bound C 34 S cores in the mass range from 600 M ⊙ to 2000 M ⊙ ." (5.3.)
   - fitting: single power law; chi2/dof in Table 2; sampler/priors not stated  
  > "The best-fit parameters of a single power-law for the CMFs." (Table 2)
   - validation: compared with Orion A index 2.3±0.1  
  > "which is smaller than that of 2 . 3 ± 0 . 1 in the Orion A (Ikeda et al. 2007)" (5.3.)

## Software

- **CASA** : data reduction, concat, clean, feathering  
  > "reduced using the pipeline script in the CASA software (McMullin et al. 2007)" (2. OBSERVATION)
- **clumpfind** : 3D core identification  
  > "using the clumpfind algorithm (Williams et al. 1994)" (4.1.)
- **RADEX** : LVG excitation temperature  
  > "Using the RADEX LVG (Large Velocity Gradient) algorithm (van der Tak et al. 2007)" (4.2. Mass estimation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H13CO+ core candidates | 3293 | not stated | cores | 2 | Finally, we identified 3293 core candidates in the H 13 CO + data and 3192 core candidates in the C 34 S data |
| bound H13CO+ cores (alpha<2) | 241 | not stated | cores | 4 | The 241 bound cores were identified. |
| bound C34S cores | 129 | not stated | cores | 4 | 129/3192 |
| CMF index H13CO+ whole 50MC | 1.48 | 0.14 | dimensionless | 5 | The best-fit α cmf value is 1 . 48 ± 0 . 14 |
| CMF index C34S | 1.15 | 0.24 | dimensionless | 5 | The best-fit α cmf value is 1 . 15 ± 0 . 24. |
| CMF index H13CO+ CCC / non-CCC | 1.38 / 1.37 | 0.20 / 0.13 | dimensionless | 5 | The best-fit values of α cmf in the CCC and non-CCC regions are 1 . 38 ± 0 . 20 and 1 . 37 ± 0 . 13, respectively. |
| mean mass bound H13CO+ cores CCC / non-CCC | 1300 / 610 | 970 / 510 | Msun | 4 | are 1300 ± 970 M ⊙ and 190 − 4500 M ⊙ , respectively |
| total LTE mass of 50MC (H13CO+) | 1.3e6 | factor ~2 abundance | Msun | 3 | The total LTE mass of the 50MC is 1 . 3 × 10 [6] M ⊙ from the H 13 CO + J = 1 − 0 channel maps |
| bound core mass fraction in CCC | 68% (H13CO+), 76% (C34S) | not stated | percent | 4 | The total bound core mass in the CCC region is 68 %(= 1 . 6 × 10 5 M ⊙ / 2 . 3 × 10 5 M ⊙ ) |

## Qualitative findings

- Filamentary structures are ubiquitous in the 50MC, suggesting also in CMZ clouds  
  > "The existence of a number of the filamentary structures in the 50MC strongly suggests that the filamentary structures are also ubiquitous in the molecular clouds in the CMZ." (3. CHANNEL MAPS)

## Claim tuples

- H: CCC compresses gas and increases dense bound cores | E: Compare bound cores in R_T>2.5 CCC region vs non-CCC | R: Similar bound core numbers in a ~14% area; higher densities in CCC; 26 cores >8.1e23 cm^-2 only in CCC | F: CCC compresses gas and increases number of dense bound cores | **supported**
- H: CCC changes the CMF slope | E: Power-law fits in CCC and non-CCC | R: 1.38±0.20 vs 1.37±0.13 | F: Slope unchanged but massive cores form only in CCC | **supported**
- H: 50MC cores are more top-heavy than Orion A | E: Compare CMF indices | R: 1.48±0.14 vs 2.3±0.1 | F: Top-heavy CMF | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Bound cores defined as alpha<2 because abundance uncertainty of factor 2  
  > "we consider the H 13 CO + core candidates with the virial parameters of less than 2 as ”bound cores”" (5.1. Identification of Bound cores)
- How they decided it was enough: _not stated_
- Limitation (authors): Abundance uncertainty up to a factor of 2 affects masses  
  > "Because the uncertainty of the abundance that is used to estimate the mass is up to a factor of 2" (4.2. Mass estimation)
- Caveat (inferred, ours): Tex per core from a single LVG fit of C32S over a large region may be unreliable
- Caveat (inferred, ours): Virial analysis ignores external pressure and magnetic fields
- Caveat (inferred, ours): CMF fit has few bins and low dof
- Caveat (inferred, ours): CCC region defined by R_T threshold chosen to cover masers; selection could bias comparisons
- Caveat (inferred, ours): Virial parameters 10-100x Orion, so most candidates unbound; bound selection alpha<2 is abundance dependent

## Reproducibility

- Data public (paper): ALMA project data acknowledged; channel maps hosted on author website  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00080.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters (mask, threshold, cell, image size)
- Missing: feathering details
- Missing: machine-readable core catalog (only truncated tables)
- Missing: CMF fitting procedure
- Data volume (inferred): Large: 12m mosaic of 137 pointings, ACA and TP, ~hundreds of GB raw
- Score (inferred): 5/5, Data public and algorithm clear, but imaging details and Tex assignment are underspecified.
- Rediscovery candidate: no, Recipe incomplete in imaging and fitting details and requires large mosaic data.

## Links

- Method: Williams et al. 1994 (clumpfind algorithm)
- Method: van der Tak et al. 2007 (RADEX)
- Companion: Tsuboi et al. 2015 (CCC proposal and earlier CMF in 50MC)
- Companion: Ikeda et al. 2007 (Orion A core comparison sample)
- Related: ALMA cycle 1 2012.1.00080.S

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
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
  "stated": 45,
  "rate": 0.608
 },
 "evidence_ok": true
}
```
