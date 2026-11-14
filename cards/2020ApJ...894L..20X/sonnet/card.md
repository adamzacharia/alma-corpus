# Independent Core Rotation in Massive Filaments in Orion

`2020ApJ...894L..20X` | The Astrophysical Journal Letters 2020 | first author: Xu, Xuefang | arXiv: 2004.14643 | DOI: 10.3847/2041-8213/ab8ad7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: Are the rotation axes of dense cores in OMC-2/OMC-3 aligned with their host filaments, and how much angular momentum and rotational support do the cores have?  
  > "In this work, we focus on the angular momentum of cores and its relation with respect to filaments." (Introduction)
- Target **OMC-2 and OMC-3 filaments and 30 cores**: coordinates map center 5:35:21.0, -5:00:00 (J2000); core positions in Table 1  
  > "We adopt a distance of 400 pc for OMC-2 and OMC-3 following (cite: nutter2007)." (Introduction); "center position (5$^{h}$:35$^{m}$:21.0$^{s}$, -5$^{\circ}$:00$^{'}$:00$^{''}$) of the combined N$_{2}$H$^{+}$ images" (4.1 Fitting spectral lines and velocity gradient); z/distance 400 pc  
  > "We adopt a distance of 400 pc for OMC-2 and OMC-3 following (cite: nutter2007)." (Introduction); "center position (5$^{h}$:35$^{m}$:21.0$^{s}$, -5$^{\circ}$:00$^{'}$:00$^{''}$) of the combined N$_{2}$H$^{+}$ images" (4.1 Fitting spectral lines and velocity gradient); distance from Nutter & Ward-Thompson 2007  
  > "We adopt a distance of 400 pc for OMC-2 and OMC-3 following (cite: nutter2007)." (Introduction); "center position (5$^{h}$:35$^{m}$:21.0$^{s}$, -5$^{\circ}$:00$^{'}$:00$^{''}$) of the combined N$_{2}$H$^{+}$ images" (4.1 Fitting spectral lines and velocity gradient)

## Data provenance

- ALMA projects: 2013.1.00662.S
- bands: Band 3  
  > "We mapped OMC-2 and OMC-3 in N$_{2}$H$^{+}$ (1–0) with ALMA in November 2014 and August 2015 in band 3." (2 Data)
- frequencies and spectral setup: 35 kHz channel width, 0.11 km/s at 93 GHz  
  > "The frequency resolution of N$_{2}$H$^{+}$ is 35 kHz, which corresponds to a velocity resolution of 0.11 km$\,s^{-1}\,$ at 93 GHz." (2 Data)
- continuum bandwidth: _not stated_
- arrays: 12-m main array and ACA; mosaics of 11 pointings (OMC-3) and 7 pointings (OMC-2)  
  > "We used the 12-m main array and the Atacama Compact Array (ACA) to mosaic OMC-3 with 11 pointings, and OMC-2 with 7 pointings." (2 Data)
- configurations: _not stated_
- baselines: 12-m: 13.6–340.0 m; ACA: 6.8–87.4 m  
  > "The baselines of the 12-m main array and the ACA observations are at a range of 13.6 – 340.0 m and 6.8 – 87.4 m, respectively." (2 Data)
- angular resolution: ~3 arcsec (~0.006 pc)  
  > "The N$_{2}$H$^{+}$ (1–0) images have an angular resolution of $\sim$ 3$^{"}$" (2 Data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: November 2014 and August 2015  
  > "with ALMA in November 2014 and August 2015 in band 3" (2 Data)
- pi or archival as stated: _not stated_
- Line: N2H+ J=1-0 (not stated (~93 GHz))
- Other facility **Nobeyama 45m (NRO Star Formation Legacy Project, FOREST)**: Single-dish N2H+ (1-0) data combined with ALMA to recover missing flux  
  > "The single dish data of N$_{2}$H$^{+}$ (1–0) were taken from the NRO (Nobeyama Radio Observatory) Star Formation Legacy Project (cite: nakamura2019)." (2 Data)
- External data: Core masses and virial masses  
  > "The values of Mass and Mass$_{vir}$ are from (cite: lid2013)." (Table 1) [from (cite: lid2013)]
- External data: Core major and minor axes  
  > "Major and Minor axes are from (cite: nutter2007)." (Table 1) [from (cite: nutter2007)]

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
- array combination: ALMA (12m+ACA) combined with Nobeyama single-dish in CASA  
  > "The combination was performed using CASA (Common Astronomy Software Applications) (cite: mcmullin2007)." (2 Data)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Filament orientation fitting via autocorrelation function  
  > "fit them following the procedures described in (cite: lihb2013)" (3.1 Orientations of the filaments) [from (cite: lihb2013)]
- Velocity gradient fitting method  
  > "measure the velocity gradients following the method described in (cite: goodman1993)" (3.2) [from (cite: goodman1993)]
- Monte Carlo angle simulation details  
  > "The details of the Monte Carlo simulations can be found in Appendix A of (cite: stephens2017)." (4.1) [from (cite: stephens2017)]

### Not stated but needed to reproduce (our reading)

- CASA version and combination task/parameters (feather vs. other), weights and scaling
- Calibration and imaging details (pipeline, weighting, cleaning, mosaic, final beam, rms)
- How core radii R and core extent for the gradient fit were defined
- Method for deriving the uncertainties on G and theta_G
- How the 3D random simulation was projected to 2D
- Which filament segment orientation was assigned to each core

## Analysis recipe

1. **combine ALMA and Nobeyama data**: Combined interferometric and single-dish N2H+ cubes in CASA to recover missing flux  
  > "We combined the N$_{2}$H$^{+}$ data from ALMA and Nobeyama to recover missing fluxes in the interferometric data." (2 Data)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **measure filament orientation**: Autocorrelation of integrated intensity map via FFT; least-squares long-axis fit to the contour at 20% of peak  
  > "For a given contour of this autocorrelation map, the long axis direction ($\theta_{f}$) can be obtained by performing a least-squares fit to the pixel positions located within the contour." (3.1)
   - parameter: 20% contour of peak  
  > "In subsequent calculations, the contour at 20% of the peak value was adopted." (3.1)
   - fitting: _not stated_
   - validation: Variation of < 5 deg among contour levels  
  > "only $< 5^{\circ}$ variation was found among different trials" (3.1)
3. **fit velocity gradients of cores**: Single Gaussian fit to the isolated hyperfine component, then planar fit v_LSR = v0 + a dα + b dδ  
  > "We then fit the velocity field as $v_{LSR} = v_0 + a \Delta \alpha + b \Delta \delta$" (3.2)
   - parameter: Require peak > 3 rms and fitting errors  
  > "we require the spectral lines to have peak intensity greater than three times of the Root Mean Square (rms) noise" (3.2)
   - assumption: Distance 400 pc  
  > "We adopt a distance of 400 pc for OMC-2 and OMC-3" (Introduction)
   - fitting: _not stated_
   - validation: Single-Gaussian fit compared with fitting all hyperfine components; no significant difference  
  > "we compared fitting all hyperfine components and fitting just the isolated one with a single Gaussian. No significant difference was found." (3.2)
4. **test alignment of rotation and filaments**: Compare |θf−θG| with 3D random-vector Monte Carlo projected to 2D using an Anderson-Darling test  
  > "10$^{6}$ pairs of unit vectors are generated to produce 10$^{6}$ angles of $\theta_{3D}$" (4.1)
   - fitting: _not stated_
   - validation: AD p-value 0.97 vs random  
  > "the AD test gives a $p$–value of 0.97, consistent of being random" (4.1)
5. **derive J/M and beta**: J/M = 0.59 G R^2 and beta = 0.34 G^2 R^3/(GM)  
  > "J/M =  0.59{}{\cal G} R^{2}" (4.2)
   - assumption: Power-law density profile rho ∝ R^-1.6  
  > "cores have a power-law profile density ($\rho \propto R^{-1.6}$)" (4.2)
   - fitting: _not stated_
   - validation: Slope compared with 1.6 from Goodman et al. 1993  
  > "The slope is consistent with the index value of 1.6 found by  (cite: goodman1993)" (4.2)

## Software

- **CASA** : Combining ALMA and Nobeyama data  
  > "The combination was performed using CASA (Common Astronomy Software Applications) (cite: mcmullin2007)." (2 Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Core velocity gradient range | 1.3 to 16.7 | not stated | km/s/pc | 3 | The measured 2D velocity gradients of cores are between 1.3 and 16.7 km s$^{-1}$ pc$^{-1}$ |
| J/M range | 0.0012 to 0.016 | not stated | pc km/s | 5 | specific angular momentum ($J/M$) between 0.0012 and 0.016 pc km s$^{-1}$ |
| J/M power-law index vs R | 1.52 | 0.14 | dimensionless | 5 | $J/M \propto R^{1.52~\pm~0.14}$ |
| beta range | 0.00041 to 0.094 | not stated | dimensionless | 5 | ranges from 0.00041 to 0.094 |
| AD test p-value vs random distribution | 0.97 | not stated | dimensionless | 4 | the AD test gives a $p$–value of 0.97 |
| Cores parallel to filament (0±10 deg) | 7 (~23%) | not stated | cores | 4 | the gradient directions of 7 cores ($\sim$23%) are essentially parallel to their filament orientations |
| Cores perpendicular to filament (90±10 deg) | 8 (~27%) | not stated | cores | 4 | the gradient directions of 8 cores ($\sim$27%) are essentially perpendicular to their filaments |

## Qualitative findings

- Rotation provides insignificant support against gravitational collapse (small beta).  
  > "these small values of $\beta$ indicate that rotation alone is not enough to support the core from collapsing due to gravity" (4.2)

## Claim tuples

- H: Core rotation axes are correlated with host filament elongation | E: Compared |θf−θG| for 30 cores with a 3D random Monte Carlo distribution using an AD test | R: AD p = 0.97 versus random | F: Core rotation axes are independent of the filament orientation | **supported**
- H: Specific angular momentum scales with core size | E: Computed J/M from gradients and fitted a power law vs R | R: J/M ∝ R^1.52±0.14 | F: Consistent with the index 1.6 of Goodman et al. 1993 | **supported**
- H: Rotation supports cores against collapse | E: Computed beta, the ratio of rotational to gravitational energy | R: beta from 0.00041 to 0.094 | F: Rotation is insufficient to prevent collapse | **refuted**

## Reasoning

- Why this data: N2H+ (1-0) traces cold dense gas and ALMA resolution reaches the thermal Jeans scale  
  > "making N$_{2}$H$^{+}$ (1–0) especially suitable for tracing dense cores and filaments" (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Differences in methods and samples among studies; a much larger sample is needed to tackle the issue systematically.  
  > "high spectral and spatial images of a much larger sample are needed to tackle the issue systematically" (5 Discussion)
- Caveat (inferred, ours): Only 2D projected angles with a coarse 3D random model; the p-value of 0.97 with N=30 has limited power
- Caveat (inferred, ours): Single-Gaussian fits and gradient direction can be affected by outflows and infall
- Caveat (inferred, ours): Core sizes and masses are taken from other works with different resolution
- Caveat (inferred, ours): The beta and J/M uncertainties are dominated by the density profile assumption

## Reproducibility

- Data public (paper): ALMA project code is given; the Nobeyama data come from the NRO legacy project  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00662.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and combination parameters
- Missing: Imaging parameters
- Missing: Definition of core radius R and the pixels used per core
- Missing: Code for the Monte Carlo and fits
- Data volume (inferred): ~50-200 GB raw (12m + ACA mosaics); Nobeyama cubes small
- Score (inferred): 3/5, Public data and a clear analysis chain, but the combination and imaging parameters and the core-region definitions are missing.
- Rediscovery candidate: no, Combination and imaging details are not stated, and the core inputs depend on external tables.

## Links

- Method: (cite: goodman1993) (velocity gradient method)
- Method: (cite: lihb2013) (filament orientation method)
- Method: (cite: stephens2017) (Monte Carlo angle simulations)
- Companion: (cite: lid2013) (core masses and temperatures)
- Companion: (cite: nakamura2019) (Nobeyama N2H+ data)
- Related: NRO Star Formation Legacy Project

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
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
  "facts": 71,
  "stated": 35,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
