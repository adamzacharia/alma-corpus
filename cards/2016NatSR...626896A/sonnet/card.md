# Kennicutt-Schmidt Law in the Central Region of NGC 4321 as Seen by ALMA

`2016NatSR...626896A` | Scientific Reports 2016 | first author: Azeez, Jazeel H. | arXiv: - | DOI: 10.1038/srep26896

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, star_formation
- Question: Does the Kennicutt-Schmidt relation between SFR surface density and molecular/atomic gas surface density hold on sub-galactic scales in the center, upper arm and lower arm of NGC 4321?  
  > "The relationship between the surface density of molecular gas mass ∑H 2 and that of star formation rate ∑SFR has been investigated" (abstract)
- Target **NGC 4321 (M100)**: coordinates mosaic centers RA = 12:22:54.6, Dec = +15:48:56.5 (12-m)  
  > "central region of NGC 4321 (also known as M100) at the distance of 17.1 Mpc" (abstract); "the distance of 17.1 Mpc taken from (Yuan and Kuo)" (2 Data); z/distance 17.1 Mpc; z = 0.005  
  > "central region of NGC 4321 (also known as M100) at the distance of 17.1 Mpc" (abstract); "the distance of 17.1 Mpc taken from (Yuan and Kuo)" (2 Data); distance from Yuan and Kuo (cite: 12)  
  > "central region of NGC 4321 (also known as M100) at the distance of 17.1 Mpc" (abstract); "the distance of 17.1 Mpc taken from (Yuan and Kuo)" (2 Data)

## Data provenance

- ALMA projects: 2011.0.00004.SV
- bands: Band 3 (~2.6 mm)  
  > "with band 3 (λ ~ 2.6 mm) receivers" (2 Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m, 7-m and total power arrays  
  > "The third one is the single dish data for NGC 4321, which was taken on July 1, 5, 7 and 17, 2014, with a total power array." (2 Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 3.87″ × 2.53″ (feathered CO image)  
  > "The restoring beam of the CO feather image for M100 is 3.87 ″ × 2.53″" (2 Data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 12-m: 10 Aug and 10 Sep 2011; 7-m: 17-18 Mar, 14 Apr, 11 May 2013; TP: July 2014  
  > "with 12-m array on August 10 and September 10, 2011" (2 Data)
- pi or archival as stated: ALMA cycle-0 science verification data  
  > "NGC 4321 has been observed using ALMA (Atacama Large Millimeter = Submillimeter Array) in the cycle-0 science verification data" (2 Data)
- Line: 12CO J=1-0 (not stated)
- Other facility **VLA (project AS0750)**: HI 21-cm D-configuration data  
  > "The HI data of spiral galaxy NGC 4321 were obtained from the Very Large Array (VLA) data archive with project number AS0750" (2 Data)
- Other facility **Spitzer IRAC**: 3.6 and 8 μm images for SFR  
  > "The infrared data are obtained from the Spitzer Space Telescope Infrared Array Camera (IRAC) 3.6 and 8 μm images" (Relationship between Gas Mass Density and Star Formation)
- External data: CO-to-H2 conversion factor X = 2.3e20 cm-2 (K km/s)-1  
  > "X = 2.3 × 10 [20] cm [−][2] (K km s [−][1] ) [−][1] (see Burillo _et al._ [30] )" (Gas Mass and Surface Density) [from Garcia-Burillo et al. (cite: 30)]
- External data: η8 = 0.232 for stellar subtraction  
  > "where η 8 = 0.232 [36]" (Relationship between Gas Mass Density and Star Formation) [from Helou et al. (cite: 36)]

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

- task: VLA HI: CASA CLEAN, Briggs weighting, CELL=15″, IMSIZE=64  
  > "The visibility data were cleaned in CASA using the task CLEAN." (2 Data)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: UVCONTSUB for HI  
  > "using the task UVCONTSUB, which removed the continuum emission from the u,v data of all channels" (2 Data)
- line free channels: _not stated_
- primary beam correction: applied to HI cube  
  > "then by applying primary beam correction" (2 Data)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: CO 3.87″ × 2.53″; HI 52.98″ × 47.5″  
  > "at the resolution of 52.98″ × 47.5″" (Line Emission Distribution)
- final rms: HI channel rms 0.99 mJy/beam  
  > "The rms noise in the channel map is 0.99 mJy beam [−][1]" (Line Emission Distribution)

### Inherited from earlier work

- SFR from 8 μm dust luminosity and dust subtraction equations  
  > "The star formation surface density (∑SFR) is derived from the 8 μm dust luminosity [29]" (Relationship between Gas Mass Density and Star Formation) [from Tsai et al. (cite: 29)]

### Not stated but needed to reproduce (our reading)

- CO calibration/imaging details (CASA version, weighting, feathering, channel width, masking, clipping)
- How the 8 μm and 3.6 μm fluxes were measured per box and any aperture/convolution to matching resolution
- Conversion of 8 μm flux to luminosity numerical constants
- Velocity range for CO moment map
- Rest frequency of CO
- Why Table 2 has 174 boxes vs stated geometry

## Analysis recipe

1. **Make CO and HI maps**: CO feathered integrated intensity map; HI cube cleaned and moment-0 via IMMOMENTS  
  > "A channel map was used as input for the CASA task IMMOMENTS to calculate the total HI (zeroth moment) map." (2 Data)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive gas masses and surface densities in boxes**: CO flux to H2 mass with Galactic X factor; HI mass from flux integral; 174 CO boxes of 4″×4″ and HI boxes of 55″  
  > "The central 14.5 kpc region of the NGC 4321 galaxy is divided into 174 regions covering the nucleus (black boxes), lower arm (red boxes) and upper arm (yellow boxes)" (Gas Mass and Surface Density)
   - assumption: X_CO = 2.3e20, D = 17.1 Mpc, helium excluded  
  > "The surface density values are in terms of hydrogen alone, i.e. the contribution of Helium hasn’t been included." (Gas Mass and Surface Density)
   - fitting: _not stated_
   - validation: Compared central mass with IRAM and JCMT values, concluding no missing flux  
  > "This result indicates that no missing flux exists in the central region at _r_ = 30″." (Gas Mass and Surface Density)
3. **Derive SFR surface density from Spitzer**: Subtract starlight (η8 × 3.6 μm) from 8 μm, convert dust luminosity to SFR  
  > "To enhance the visibility of the dust features, the contribution from starlight (measured at 3.6 μm) has been subtracted from the 8 μm image." (Relationship between Gas Mass Density and Star Formation)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit K-S relation per region**: Ordinary least squares in log space for center, upper and lower arms  
  > "For each region ordinary least square fitting was used." (Relationship between Gas Mass Density and Star Formation)
   - software: python
   - fitting: OLS; uncertainties are fitting errors  
  > "The uncertainties for the slope and the intercept for each region are calculated using python, they refer to the fitting error." (Relationship between Gas Mass Density and Star Formation)
   - validation: Correlation coefficient r = 0.69  
  > "The correlation coefficient _r_ = 0.69 with 99.9% probability." (Relationship between Gas Mass Density and Star Formation)

## Software

- **CASA** 4.1 (for HI): HI calibration/imaging and ALMA analysis  
  > "The data were calibrated and reduced in the CASA 4.1 data processing package." (2 Data)
- **python** : fit uncertainties  
  > "The uncertainties for the slope and the intercept for each region are calculated using python" (Relationship between Gas Mass Density and Star Formation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| K-S index, center | 1.13 | 0.20 | dimensionless | 4 | equal to 1.13 ± 0.20 with intercept −3.71 ± 0.53 |
| K-S index, lower arm | 0.8 | 0.14 | dimensionless | 4 | the index of K-S is 0.8 ± 0.14 with intercept −2.86 ± 0.3 |
| K-S index, upper arm | 0.36 | 0.08 | dimensionless | 4 | approximately 0.36 ± 0.08 with intercept 1.93 ± 0.15 |
| Total M(H2) in 200″×200″ | 0.9e10 | not stated | Msun | 2 | is equal to 0.9 × 10 [10] M ⊙ at D = 17.1 Mpc |
| M(H2) within r=30″ | 3.1e9 | not stated | Msun | 2 | The molecular gas mass in the center region at _r_ = 30″ is equal to 3.1 × 10 [9] M ⊙ |
| Total M(HI) | 3.02e9 | not stated | Msun | 2 | The total _M_ ( _HI_ ) = 3.02 × 10 [9] M ⊙ is found at the assumed distance of 17.1 Mpc. |

## Qualitative findings

- Center and arm SFR surface densities resemble starburst galaxies yet follow the same star formation law  
  > "The star formation rate surface density of the center and spiral arm regions of NGC 4321 are similar to those of starburst galaxies" (Relationship between Gas Mass Density and Star Formation)

## Claim tuples

- H: The central region follows the traditional K-S law | E: OLS fit of ΣSFR vs ΣH2 in 4″ boxes | R: index 1.13±0.20 | F: Consistent with the traditional K-S law and constant SFE | **supported**
- H: Arms follow the same law | E: Separate fits for lower and upper arm | R: 0.8 and 0.36 | F: Sub-linear indices, with the upper arm very low, possibly sub-thermal gas | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): No direct measurement of the conversion factor in M100, so mass may be in error  
  > "A direct measurement is unavailable for the conversion factor in M100." (Gas Mass and Surface Density)
- Caveat (inferred, ours): Surface-density boxes are tiny and may be correlated/oversampled relative to 3.9″ beam
- Caveat (inferred, ours): SFR from 8 μm with no uncertainty or resolution matching
- Caveat (inferred, ours): OLS ignores errors in both variables; fit errors only
- Caveat (inferred, ours): Inconsistent distances (13.8 vs 17.1 Mpc) and box counts (24 vs 61 HI regions)
- Caveat (inferred, ours): Galactic X factor in a central region

## Reproducibility

- Data public (paper): ALMA SV data and VLA archive data  
  > "obtained from the Very Large Array (VLA) data archive with project number AS0750" (2 Data)
- Products in archive: _not stated_
- Missing: CO imaging parameters and box definitions
- Missing: Spitzer flux extraction and SFR constants
- Data volume (inferred): ~50-100 GB for ALMA SV plus VLA
- Score (inferred): 4/5, Public data and simple analysis but imaging and SFR steps underspecified.
- Rediscovery candidate: no, Key steps (CO imaging, Spitzer photometry, box placement) not specified enough to reproduce the numbers.

## Links

- Method: Tsai et al. (cite: 29) (SFR and dust-subtraction recipe)
- Related: ALMA Cycle-0 Science Verification
- Related: VLA AS0750

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
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
  "facts": 65,
  "stated": 32,
  "rate": 0.492
 },
 "evidence_ok": true
}
```
