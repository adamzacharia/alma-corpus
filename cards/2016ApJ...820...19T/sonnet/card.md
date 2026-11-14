# Mapping CO Gas in the GG Tauri A Triple System with 50 au Spatial Resolution

`2016ApJ...820...19T` | The Astrophysical Journal 2016 | first author: Tang, Ya-Wen | arXiv: 1511.05687 | DOI: 10.3847/0004-637X/820/1/19

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What physical mechanisms (e.g. embedded proto-planet) shape the gas in the GG Tau A circumternary disk, as seen in CO radial structure and the hot spot?  
  > "We aim to unveil the observational imprint of physical mechanisms that govern planetary formation in the young, multiple system GG Tau A." (abstract)
- Target **GG Tau A**: coordinates _not stated_; z/distance 1"36 = 191 AU (implies ~140 pc; distance not given explicitly)  
  > "The massive circum-ternary Keplerian disk surrounding GG Tau Aa, Ab1 and Ab2 (cite: difolco14) consists of a dense gas and dust annulus or ring" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00129.S
- bands: Band 7  
  > "GG Tau A was observed with the ALMA Band 7 receiver during Early Science" (2.1 Observations)
- frequencies and spectral setup: 12CO and 13CO 3-2 at 345.8 and 330.6 GHz, two SPWs with 1920 channels of 35.3 kHz and 58.6 MHz bandwidth; two continuum SPWs with 3840 channels, 1.875 GHz bandwidth each  
  > "each providing 1920 channels of 35.3 kHz effective resolution ($\sim 0.031$ km/s) and 58.6 MHz bandwidth." (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 1282 m, 29 antennas  
  > "The array included 29 antennas with projected baselines ranging from 15 m to 1282 m." (2.1 Observations)
- angular resolution: 0.41x0.33" (12CO), 0.43x0.34" (13CO), 0.39x0.35" (continuum), robust weighting  
  > "0"41$\times$0"33 with position angle (P.A.) of 52$\ensuremath{^\circ}$" (2.2 Results)
- max recoverable scale: _not stated_
- sensitivity: 9.6 mJy/beam (0.9 K) per 35.3 kHz channel for lines; 0.2 mJy/beam continuum  
  > "The achieved sensitivity for the 0.9 mm continuum observations is 0.2 mJy/beam." (2.2 Results)
- time on source: _not stated_
- observing dates: November 18 and 19, 2013, three execution blocks  
  > "Observations were made in three execution blocks on November 18 and 19, 2013." (2.1 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO 3-2 (345.8 GHz)
- Line: 13CO 3-2 (330.6 GHz)
- Other facility **PdBI**: IRAM 12CO 2-1 data used in earlier work (listed under Facilities)  
  > "*Facilities:* PdBI, ALMA." (Summary)
- External data: 12CO 6-5 and 2-1 results, hot spot detection  
  > "a puzzling CO “hot spot" was detected at the outer edge of the dense ring at a radius of $\simeq$ 260 AU." (Introduction) [from (cite: dutrey14)]
- External data: 13CO abundance 1.4e-6  
  > "a $^{13}$CO abundance of 1.4$\times$10$^{-6}$ (cite: dutrey96)" (3.1 CO radial distributions) [from (cite: dutrey96)]
- External data: H2 density 1e6 to 1e9 cm-3 in ring and outer disk  
  > "The H$_{2}$ density within the ring and outer disk is estimated to be large, being 10$^6$ to 10$^9$ cm$^{-3}$ (cite: guilloteau99)." (3.3 Excitation conditions) [from (cite: guilloteau99)]

## Processing

### Calibration

- pipeline or manual: CASA calibration (bandpass, phase, amplitude, flux)  
  > "The calibration (bandpass, phase, amplitude, flux) was performed using CASA[^1] v4.1." (2.1 Observations)
- casa version: CASA v4.1  
  > "was performed using CASA[^1] v4.1." (2.1 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120, ~1.4 Jy at 343.5 GHz  
  > "The bandpass calibration was done using J0423-0120 (aka J0423-013, flux $\sim$ 1.4Jy at 343.5GHz), which also provided the flux scale." (2.1 Observations)
- flux scale uncertainty: _not stated_
- self calibration: Continuum self-calibration, applied to line data  
  > "A high dynamic range was obtained by self-calibrating the continuum data and applying this solution to the line data." (2.2 Results)

### Imaging

- task: GILDAS used to generate CO and continuum maps  
  > "CO and continuum maps were generated from the visibility data using the GILDAS[^2] package." (2.2 Results)
- deconvolver: _not stated_
- weighting robust: robust weighting (value not given); natural weighting for spectra  
  > "the results and maps presented in this paper use a robust weighting with the exception of the spectra presented in Sec.[3.2](#ana:co_dyn)." (2.2 Results)
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

- Proper motion correction (17, -19) mas/yr  
  > "All results have been corrected for the source proper motion (17, -19) mas yr$^{-1}$ (cite: ducourant05; dutrey14)" (2.2 Results) [from (cite: ducourant05; dutrey14)]

### Not stated but needed to reproduce (our reading)

- robust parameter value
- cell and image size
- clean masks and deconvolution settings
- self-calibration solution intervals
- line-free channels / continuum subtraction
- source distance
- Gaussian ring fitting details and azimuthal sector definitions
- circumplanetary disk mass formula
- spectrum extraction locations coordinates

## Analysis recipe

1. **Image and self-calibrate**: GILDAS imaging after CASA calibration; continuum self-cal applied to lines  
  > "A high dynamic range was obtained by self-calibrating the continuum data and applying this solution to the line data." (2.2 Results)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Radial profiles of de-projected moment 0 and Gaussian decomposition**: Western-side averaged radial profile decomposed into partially overlapping Gaussians  
  > "The radial profile for the western half of the disk is decomposed into a series of partially overlapping Gaussians for both CO lines." (3.1 CO radial distributions)
   - parameter: rotation axis 7.5 deg East of North as azimuth reference  
  > "The disk rotation axis, which is 7.5$\ensuremath{^\circ}$ East of North, is used as the azimuthal reference" (3.1 CO radial distributions)
   - fitting: _not stated_
   - validation: formal errors only  
  > "The positions of the peaks (distance from center in AU) and widths (FWHM in AU) of these Gaussians and their corresponding formal errors are presented in Figure [3](#fig:cocut)b and c." (Analysis of the CO radial distribution, CO radial distributions)
3. **Excitation: temperature and column density**: Optically thick brightness temperature gives kinetic temperature; RADEX for 13CO column density; 12CO/13CO ratio for hot spot  
  > "We further estimate the column density using RADEX[^3] (cite: van07)." (3.3 Excitation conditions)
   - software: RADEX
   - parameter: line width 0.3 km/s, T = 20 K  
  > "assuming a line width of 0.3 km/s" (3.3 Excitation conditions)
   - assumption: isotopologue ratio 70, beam filling factor f=1, thermalized lines  
  > "an isotologue ratio of 70" (3.3 Excitation conditions)
   - fitting: _not stated_
   - validation: consistent with Guilloteau et al. 1999 values  
  > "This N($^{13}$CO) is consistent with the analysis from (cite: guilloteau99)." (3.3 Excitation conditions)

## Software

- **CASA** v4.1: calibration  
  > "was performed using CASA[^1] v4.1." (2.1 Observations)
- **GILDAS** : imaging of CO and continuum  
  > "CO and continuum maps were generated from the visibility data using the GILDAS[^2] package." (2.2 Results)
- **RADEX** : 13CO column density  
  > "We further estimate the column density using RADEX[^3] (cite: van07)." (3.3 Excitation conditions)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust ring inner radius | 1.36 (191) | negligible formal errors | arcsec (AU) | 1 | 1$\ensuremath{''}$36 (191 AU), 1$\ensuremath{''}$90 (266 AU), 7.5$\ensuremath{^\circ}$ and $36.4\ensuremath{^\circ}$ |
| Dust ring outer radius | 1.90 (266) | negligible formal errors | arcsec (AU) | 1 | 1$\ensuremath{''}$36 (191 AU), 1$\ensuremath{''}$90 (266 AU), 7.5$\ensuremath{^\circ}$ and $36.4\ensuremath{^\circ}$ |
| Gas temperature in outer disk (locations 12-14) | 16-19 | ~1 K formal | K | 3 | The gas temperature at locations 12 to 14 is then 16-19 K with typical formal errors of 1 K |
| Hot spot kinetic temperature | 45 | not stated | K | 3 | the kinetic temperature is $45$ K, and N($^{13}$CO) $\approx 2\times10^{15}$cm$^{-2}$ |
| Hot spot N(13CO) | 2e15 | not stated | cm^-2 | 3 | the kinetic temperature is $45$ K, and N($^{13}$CO) $\approx 2\times10^{15}$cm$^{-2}$ |
| Outer disk N(13CO) | >3e15 | lower limit | cm^-2 | 3 | the column density N($^{13}$CO) is $>$3$\times$10$^{15}$cm$^{-2}$ |
| Gaussian ring centers in the ring/outer disk | 170-176, 240-260, 370 AU (540 AU in 12CO only) | not stated | AU | 2 | centered around 170-176 AU, 240-260 AU and 370 AU. A fourth and outermost Gaussian is observed at a radius of 540 AU, only in $^{12}$CO. |
| Embedded object mass from 13CO double peak | ~0.16 MJ (rout=10 AU); 0.016 MJ (rout=1 AU) | rough | Jupiter mass | 3 | Its mass is $\sim$0.16 Jupiter mass ($M_{\rm J}$), for an outer disk radius, r$_{\rm out}$, of 10 AU or 0.016 $M_{\rm J}$ for r$_{\rm out}$=1 AU. |

## Qualitative findings

- 12CO emission is found inside the dust cavity where no 13CO is detected.  
  > "The $^{12}$CO 3-2 emission, found within the cavity of the circumternary dust ring (at radius $< 180$ AU) where no $^{13}$CO emission is detected" (abstract)

## Claim tuples

- H: Is the outer disk radially smooth, and is it shadowed by the ring? | E: Gaussian decomposition of CO radial profiles and 12CO/13CO excitation analysis | R: Series of overlapping Gaussians; similar optically thick 12CO and 13CO intensities, T of 16-19 K | F: Unresolved gaps or dips exist and the outer disk is in the ring's shadow | **supported**
- H: Is the hot spot due to local heating, possibly by an embedded proto-planet? | E: Brightness temperature and column density at hot spot vs. disk | R: T about 45 K, at least 20 K warmer than the disk | F: Local heating likely, consistent with an embedded proto-planet, though speculative | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Stellar illumination variation and tidal disturbance by GG Tau B rejected as hot spot cause.  
  > "we find variations in stellar illumination highly unlikely to be the cause in the temperature enhancement" (4.2 The CO hot spot and its surroundings)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution does not allow detailed analysis of ring structures.  
  > "The angular resolution of these data does not allow a detailed analysis of such structures." (Summary)
- Caveat (inferred, ours): Planet interpretation is speculative and rests on a marginal double-peaked 13CO profile
- Caveat (inferred, ours): Gaussian decomposition is not unique; dips vs bumps are degenerate
- Caveat (inferred, ours): Temperature assumes beam filling factor of 1

## Reproducibility

- Data public (paper): ALMA project code printed; Cycle 1 data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00129.S ." (Acknowledgments)
- Products in archive: _not stated_
- Missing: imaging parameters in GILDAS
- Missing: Gaussian fit procedure
- Missing: spectrum locations
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 3/5, Public data and simple analysis, but imaging and fitting details are missing.
- Rediscovery candidate: no, Imaging and fitting recipes are incomplete, so the numbers are not easily redone.

## Links

- Companion: (cite: dutrey14) (ALMA 12CO 6-5 and IRAM 2-1 study that found the hot spot)

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 34,
  "rate": 0.515
 },
 "evidence_ok": true
}
```
