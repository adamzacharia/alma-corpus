# Discovery of a Molecular Collision Front in Interacting Galaxies NGC 4567/4568 with ALMA

`2018ApJ...860L..14K` | The Astrophysical Journal Letters 2018 | first author: Kaneko, Hiroyuki | arXiv: 1805.11630 | DOI: 10.3847/2041-8213/aac895

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: Is there a molecular collision front in the overlapping region of the early-stage interacting pair NGC 4567/4568, and what are the properties of the molecular gas and clouds there?  
  > "molecular gas observation of interacting galaxies at the early stage is crucial because they should maintain conditions before or at the beginning of active star formation" (Introduction)
- Target **NGC 4567/4568**: coordinates _not stated_; z/distance 16 Mpc  
  > "The pair is one of the ideal interacting galaxies for this purpose because of their alignment, vicinity (16 Mpc)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00759.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m array (36 antennas) plus ACA 7-m array  
  > "The 12-m array observations were performed using 36 antennas with C32-4 configuration." (Observations); "Observations with Atacama Compact Array (ACA), which consists of ten 7-m antennas and two 12-m antennas for Cycle 1 observation, were also requested" (Observations)
- configurations: C32-4 (12-m)  
  > "The 12-m array observations were performed using 36 antennas with C32-4 configuration." (Observations)
- baselines: _not stated_
- angular resolution: 2.0" x 2.0" (155 pc)  
  > "The combined cube has an angular resolution of 2$\ensuremath{''}$0 $\times$ 2$\ensuremath{''}$0 (equivalent to 155 pc $\times$ 155 pc at 16 Mpc)" (Observations)
- max recoverable scale: ~20" (1.55 kpc at 16 Mpc)  
  > "our ALMA data cannot detect emission from extended structures larger than $\sim$20$^{\prime\prime}$ (corresponding to 1.55 kpc at 16 Mpc)" (Observations)
- sensitivity: rms 8.5 mJy/beam; velocity resolution 5 km/s  
  > "Resultant rms noise is 8.5 mJy beam$^{-1}$." (Observations)
- time on source: 12-m: 25.4 min, 39 fields; ACA 7-m: 20.9 min  
  > "Total observed time on the source was 25.4 minutes, and 39 fields of view were required to cover whole region of the galaxy pair." (Observations); "The total on-source time for the ACA 7-m array observations as 20.9 minutes." (Observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (not stated)
- Other facility **Nobeyama 45-m telescope**: Single-dish CO data used to estimate missing flux  
  > "CO imaging with the single-dish was performed by our previous observations using the Nobeyama 45-m telescope" (Results)
- External data: Nobeyama 45-m CO flux (2.38±0.37)e3 Jy km/s and single-dish data  
  > "The CO flux of the NGC 4567/4568 system obtained with the Nobeyama 45-m telescope is (2.38 $\pm$ 0.37) $\times$ 10$^{3}$ Jy km s$^{-1}$" (Results) [from Kaneko13]
- External data: Galactic CO-H2 conversion factor 1.8e20  
  > "assuming the Galactic CO-H$_{2}$ conversion factor of 1.8 $\times$ 10$^{20}$ K (km s$^{-1}$)$^{-1}$ (cite: Dame01)" (Results) [from (cite: Dame01)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.2.1  
  > "Data reduction including calibration and imaging was made with the Common Astronomy Software Applications package (CASA) ver.4.2.1." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: not stated (bandpass J1229+0203, phase J1239+0730 for 12-m)  
  > "Bandpass and phase were calibrated with J1229+0203 (the observed flux: 6.3 Jy) and J1239+0730 (the observed flux: 0.87 Jy), respectively." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN, interactive  
  > "The imaging was done interactively using CLEAN task with Briggs weighting (robustness parameter of 0.5)." (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "The imaging was done interactively using CLEAN task with Briggs weighting (robustness parameter of 0.5)." (Observations)
- uv taper: _not stated_
- cell size: 0.5"  
  > "The final data were imaged on a 540 $\times$ 648 pixel with a grid size of 0$\ensuremath{''}$5 pixels." (Observations)
- image size: 540 x 648 pixels  
  > "The final data were imaged on a 540 $\times$ 648 pixel with a grid size of 0$\ensuremath{''}$5 pixels." (Observations)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12-m and ACA 7-m combined  
  > "The 12-m array data and the ACA 7-m array data were combined together, continuum was subtracted, and corrected for the primary beam attenuation." (Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 8.5 mJy/beam  
  > "Resultant rms noise is 8.5 mJy beam$^{-1}$." (Observations)

### Not stated but needed to reproduce (our reading)

- Line-free channels for continuum subtraction
- Clean threshold, masks and number of iterations
- Flux calibrator and flux scale uncertainty
- How ACA and 12-m data were combined (concat/weights)
- CLUMPFIND parameters (threshold, contour levels)
- Conversion from the 1.8e20 factor to the stated mass for CO (1-0) and helium inclusion
- Region definitions for filament mass and spectra averaging

## Analysis recipe

1. **Calibrate and image combined 12-m+ACA CO cube**: CASA calibration, combine 12-m and ACA, continuum subtraction, primary beam correction, interactive CLEAN  
  > "The 12-m array data and the ACA 7-m array data were combined together, continuum was subtracted, and corrected for the primary beam attenuation." (Observations)
   - software: CASA
   - parameter: Briggs robust 0.5, 0.5" pixels, 5 km/s channels  
  > "The imaging was done interactively using CLEAN task with Briggs weighting (robustness parameter of 0.5)." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate missing flux**: Compare ALMA total CO flux with Nobeyama 45-m flux  
  > "we estimated the missing flux by comparing to the data obtained with a single-dish telescope." (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Identify collision front via PVD and integrate filament**: Position-velocity diagram along PA 50 deg; integrate 2330-2380 km/s to map filament  
  > "we integrate the flux over the velocity from 2330 to 2380 km s$^{-1}$, where large velocity width is seen in Figure [2](#pvd)." (Results)
   - assumption: Galactic CO-H2 conversion factor 1.8e20 K km/s^-1  
  > "assuming the Galactic CO-H$_{2}$ conversion factor of 1.8 $\times$ 10$^{20}$ K (km s$^{-1}$)$^{-1}$ (cite: Dame01)" (Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Filament velocity dispersion and virial mass per length**: Gaussian fit to averaged spectrum; m_vir/l = 2<sigma^2>/G  
  > "We average the spectra within the filament cloud (1800 pc $\times$ 350 pc) and fit it with the Gaussian function." (Results)
   - fitting: Gaussian fit to averaged spectrum  
  > "We average the spectra within the filament cloud (1800 pc $\times$ 350 pc) and fit it with the Gaussian function." (Results)
   - validation: _not stated_
5. **Identify clouds and derive virial properties**: CLUMPFIND cloud identification; M_vir=1040 sigma^2 R, alpha_vir=5 sigma^2 R/GM, t_ff=(R^3/GM)^1/2  
  > "we identify the molecular clouds using CLUMPFIND software (cite: Williams95)." (Discussion and Conclusion)
   - software: CLUMPFIND
   - assumption: Spherical clouds with truncated rho ~ r^-1 profile  
  > "assuming that the clouds are a spherical shape with truncated $\rho \propto r^{-1}$ density profiles (cite: MacLaren88)" (Discussion and Conclusion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.1: Calibration, imaging  
  > "Data reduction including calibration and imaging was made with the Common Astronomy Software Applications package (CASA) ver.4.2.1." (Observations)
- **CLUMPFIND** : Molecular cloud identification  
  > "we identify the molecular clouds using CLUMPFIND software (cite: Williams95)." (Discussion and Conclusion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Filament velocity dispersion | 16.8 | 1.4 | km/s | 4 | Therefore the line-of-sight velocity dispersion $\sigma$ is 16.8 $\pm$ 1.4 km s$^{-1}$. |
| Filament mass | 2.24e7 | 0.07e7 | Msun | 3 | the mass is (2.24 $\pm$ 0.07) $\times$ 10$^{7} \ M_{\odot}$ |
| Missing flux fraction | 46 | 11 | % | 2 | meaning that the missing flux for the ALMA Cycle 1 observation reaches 46 $\pm$ 11 % of the total flux. |
| Total ALMA CO flux | 1.29e3 | 0.20e3 | Jy km/s | 1 | The total CO flux from the whole system obtained with the ALMA Cycle 1 observation is (1.29 $\pm$ 0.20) $\times$ 10$^{3}$ Jy km s$^{-1}$. |
| Mean virial parameter of all clouds | 0.27 | not stated | dimensionless | 5 | averaged $\alpha_{\mathrm{vir}}$ for all molecular clouds in NGC 4567/4568 is 0.27 |
| Number of clouds identified | 215 (4 in filament) | not stated | clouds | 5 | a total of 215 clouds are resolved from the cube data, and four of them are found in the filamentary structure. |

## Qualitative findings

- Molecular gas of the two galaxies connects smoothly in velocity across the overlap region, taken as evidence of a collision front; the filament coincides with an R-band dark lane.  
  > "This molecular gas having large velocity width is direct evidence of a molecular collision front, which has never been observed." (Results)

## Claim tuples

- H: A molecular collision front exists in the overlap region | E: PVD across the overlap region from the combined ALMA cube | R: Gas connects smoothly with ~50 km/s velocity width | F: Direct evidence of a molecular collision front | **supported**
- H: Clouds in the filament are gravitationally bound | E: CLUMPFIND clouds and virial parameter | R: alpha_vir 0.03-0.24 for the four clouds | F: Four clouds are bound, though the filament as a whole is unbound by m_vir/l | **supported**
- H: The filament is consistent with shock-induced giant filament simulations | E: Comparison of aspect ratio and properties with Saitoh09 | R: Aspect ratio 5 matches; mass two orders smaller | F: Filament likely shock-induced, possible super star cluster progenitor | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): No total power data; about half of the CO flux is missing, so filament size and mass are lower limits.  
  > "Note that the size and mass of the filament are a lower limit since about half of CO flux is missing as we described above." (Results)
- Caveat (inferred, ours): Virial analysis with half the flux missing may bias masses and alpha_vir
- Caveat (inferred, ours): Velocity dispersion of 16.8 km/s from a 5 km/s channel cube; low alpha_vir may reflect the CO conversion factor
- Caveat (inferred, ours): Filament virial result (unbound) vs clouds bound is not fully reconciled
- Caveat (inferred, ours): Collision-front interpretation could be chance alignment with projection effects

## Reproducibility

- Data public (paper): ALMA Cycle 1 project cited; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00759.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CLEAN masks, thresholds, line-free channels
- Missing: CLUMPFIND parameters
- Missing: Exact region definitions
- Data volume (inferred): ~20-50 GB raw for 12-m plus ACA mosaic
- Score (inferred): 5/5, Single archival project and standard CASA steps, but many imaging and CLUMPFIND details are unstated.
- Rediscovery candidate: no, Key imaging and clump-finding parameters are missing and the Nobeyama data are needed for flux comparison.

## Links

- Method: Williams95 (CLUMPFIND algorithm)
- Companion: Kaneko13 (Previous Nobeyama CO data of the pair)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
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
  "facts": 68,
  "stated": 33,
  "rate": 0.485
 },
 "evidence_ok": true
}
```
