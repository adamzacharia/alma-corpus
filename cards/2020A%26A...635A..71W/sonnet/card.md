# The Sun at millimeter wavelengths. I. Introduction to ALMA Band 3 observations

`2020A&A...635A..71W` | Astronomy and Astrophysics 2020 | first author: Wedemeyer, Sven | arXiv: 2001.02185 | DOI: 10.1051/0004-6361/201937122

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: sun
- Question: What is the diagnostic potential of ALMA Band 3 brightness temperatures for a Quiet Sun region, and how do they compare with simultaneous SDO observations?  
  > "Corresponding time series of brightness temperature maps are constructed with the first version of the Solar ALMA Pipeline (SoAP) and compared to simultaneous observations with the Solar Dynamics Observatory (SDO)." (abstract)
- Target **Quiet Sun region at disk-centre**: coordinates disk-centre, [x,y] = [0'',0''] helioprojective  
  > "The observation covers a duration of 48 min at a cadence of 2 s targeting a Quiet Sun region at disk-centre." (abstract); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00423.S
- bands: Band 3 (~100 GHz), 4 sub-bands at 93, 95, 105, 107 GHz  
  > "These sub-bands, which we refer to as sub-bands 1 – 4 (abbreviated SB1 – SB4) with increasing frequency, are centered on 93 GHz (SB1), 95 GHz (SB2), 105 GHz (SB3), and 107 GHz (SB4)" (2.1 Solar observation in Band 3)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 2 GHz per sub-band (central 1.875 GHz retained)  
  > "Each sub-band has a total bandwidth of 2 GHz (with the central 1.875 GHz being retained)" (2.1 Solar observation in Band 3)
- arrays: 52 12-m antennas plus 10 ACA 7-m antennas, plus 3 TP antennas  
  > "which included a total of 52 antennas from the 12-m Array as well as the 10 fixed 7m antennas of the Atacama Compact Array." (2.1 Solar observation in Band 3); "three TP antennas were available for fast-scan mapping." (2.1 Solar observation in Band 3)
- configurations: C40-3  
  > "an array in configuration C40-3 was used" (2.1 Solar observation in Band 3)
- baselines: 9.1 m to 492.0 m  
  > "The resulting array has baselines ranging from 9.1 m to 492.0 m" (2.1 Solar observation in Band 3)
- angular resolution: nominal 1.56''; representative beam 2.10'' x 1.37'', PA 68.0 deg  
  > "resulting in a nominal angular resolution of 1.56 $''$ and a Maximum Recoverable Scale (MRS) of 68 $''$." (2.1 Solar observation in Band 3); "has a major axis of 2.10 $''$ (full-width-half-maximum, FWHM ), a minor axis of 1.37 $''$ (FWHM ) and a position angle of 68.0 deg" (2.4 Synthesized beam)
- max recoverable scale: 68''  
  > "a Maximum Recoverable Scale (MRS) of 68 $''$." (2.1 Solar observation in Band 3)
- sensitivity: _not stated_
- time on source: 48 min, 4 scans of ~10 min, 2 s cadence  
  > "The Band 3 observing sequence consists of 4 scans with a duration of $\sim$10 min each." (2.1 Solar observation in Band 3)
- observing dates: December 22, 2016, 14:22-15:07 UT  
  > "were carried out on December 22, 2016 from 14:22UT - 15:07UT." (2.1 Solar observation in Band 3)
- pi or archival as stated: _not stated_
- Other facility **SDO (AIA, HMI)**: Co-temporal EUV/UV images and magnetograms for comparison, alignment and masks  
  > "Cotemporaneous observations with the Solar Dynamics Observatory (cite: 2012SoPh..275....3P) recorded with the Atmospheric Imaging Assembly" (2.6 Final data product and co-observations with SDO)
- Other facility **Bifrost simulation with ART**: Synthetic Band 3 brightness temperature maps for resolution test  
  > "Brightness temperature maps for ALMA Band 3 frequencies are calculated with the Advanced Radiative Transfer (ART) code" (4.2 Dependence on angular resolution)
- External data: Reference TP brightness temperature of 7300 K for Band 3 and dual-load calibration scheme  
  > "ALMA Band 3 TP maps should be scaled to a prescribed value of 7300 K." (2.5 Absolute temperatures based on Total Power maps) [from (cite: 2017SoPh..292...88W)]
- External data: Brightness temperature statistics and beams of Loukitcheva et al. and Nindos et al. for comparison  
  > "The brightness temperatures range from 5630 K to 9140 K in their time-averaged map" (4.1 Brightness temperature distribution) [from (cite: 2019ApJ...877L..26L); (cite: 2018A&A...619L...6N)]
- Simulation/model as data: Bifrost 3D radiation MHD simulation, 20 min, 1 s cadence, enhanced network; Band 3 maps via ART  
  > "The series used here has a duration of 20 min and a cadence of 1 s and features an enhanced network region in the middle with surrounding Quiet Sun." (4.2 Dependence on angular resolution)

## Processing

### Calibration

- pipeline or manual: Calibrated data from archive, processed with SoAP (CASA-based), not the official pipeline  
  > "Solar data are therefore not processed with the official ALMA pipeline. Instead, SoAP is used for this publication." (2.2 Interferometric data processing)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated data downloaded from ALMA Archive  
  > "The calibrated ALMA data were downloaded from the ALMA Archive and further processed with the Solar ALMA Pipeline" (2.2 Interferometric data processing)
- flux calibrator: _not stated_
- flux scale uncertainty: TP scale uncertainties remain; ~100 K sub-band offsets possible  
  > "suggesting offsets in the brightness temperatures of possibly on the order of 100 K." (2.5 Absolute temperatures based on Total Power maps)
- self calibration: Not applied; too aggressive for this pointing-error data  
  > "self-calibration resulted in too aggressive corrections and loss of information on small spatial scales for December 2016 data suffering from pointing errors." (2.2 Interferometric data processing)

### Imaging

- task: Multi-scale multi-frequency CLEAN in CASA, one full-band continuum image per 2 s snapshot  
  > "through application of the multi-scale (multi-frequency) CLEAN algorithm (cite: 2011A&A...532A..71R) as implemented in CASA." (2.2 Interferometric data processing)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Divide by Gaussian primary beam to threshold; final FOV 65.6'' diameter (effective thresholds 0.52 SB1, 0.44 SB4)  
  > "The resulting FOV of these maps was set to a diameter of 65.6 $''$, which corresponds to effective Gaussian thresholds of 0.52 for SB1 and 0.44 for SB4, respectively." (2.3 Interferometric field-of-view)
- array combination: Feathering of interferometric data with TP map (SB2 TP scaled to 7300 K, factor 0.979)  
  > "resulting in an applied scaling factor of 0.979 for the whole map." (2.5 Absolute temperatures based on Total Power maps)
- smoothing: _not stated_
- final beam: 2.10'' x 1.37'', PA 68.0 deg (time-averaged)  
  > "has a major axis of 2.10 $''$ (full-width-half-maximum, FWHM ), a minor axis of 1.37 $''$ (FWHM ) and a position angle of 68.0 deg" (2.4 Synthesized beam)
- final rms: _not stated_

### Inherited from earlier work

- TP dual-load calibration and 7300 K rescaling procedure  
  > "calibrated using the dual-load approach described by (cite: 2017SoPh..292...88W) as implemented in CASA" (2.5 Absolute temperatures based on Total Power maps) [from (cite: 2017SoPh..292...88W)]
- Detailed SoAP processing deferred to forthcoming paper  
  > "A detailed description of the data processing with SoAP will be provided in a forthcoming publication (cite: soap_inprep)." (2.2 Interferometric data processing) [from (cite: soap_inprep)]

### Not stated but needed to reproduce (our reading)

- SoAP code and its parameters (CLEAN scales, niter, weighting, cell/image size, masks)
- CASA version
- Data selection/flagging and reference calibrators
- Method details for SDO-ALMA co-alignment
- Thresholds used for the network/internetwork mask
- ART code settings and Bifrost snapshot identity

## Analysis recipe

1. **Reconstruct 2 s snapshot images**: Multi-scale multi-frequency CLEAN per snapshot using all four sub-bands to produce full-band maps  
  > "Here, all interferometric information from the four sub-bands is used to produce one continuum image (referred to as “full-band map”) for each time step" (2.2 Interferometric data processing)
   - software: SoAP, CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Primary beam correction, TP feathering, alignment and derotation**: Divide by Gaussian beam, feather with TP map, co-align with SDO, correct solar rotation by cross-correlating with first frame  
  > "The apparent drift of snapshot images in time due to solar rotation was then corrected by cross-correlating consecutive 2 s images with a reference image" (2.2 Interferometric data processing)
   - software: SoAP, CASA
   - parameter: TP SB2 mean in central 240'' radius scaled from 7454 K to 7300 K  
  > "The average value in the original SB2 map is 7454 K and thus only 154 K higher than the recommended value" (2.5 Absolute temperatures based on Total Power maps)
   - fitting: _not stated_
   - validation: _not stated_
3. **Brightness temperature statistics, network/internetwork**: Mask built from time-averaged AIA 1700/1600, saturated HMI magnetograms and ALMA maps; statistics in inner r<=22''  
  > "a data mask is constructed based on a combination of time-averaged maps in SDO/AIA 1700 and SDO/AIA 1600 and saturated SDO/HMI magnetograms and the band-averaged ALMA maps." (2.7 Data mask)
   - fitting: _not stated_
   - validation: _not stated_
4. **Cross-correlate ALMA with SDO channels**: Convolve SDO maps with representative ALMA beam and compute cross-correlation per time step, excluding the compact-loop region  
  > "For each time step, the SDO maps are first convolved with the representative ALMA Band 3 beam before calculating the cross-correlation" (3.4 Correlation of ALMA and SDO maps)
   - fitting: _not stated_
   - validation: _not stated_
5. **Test angular resolution effect with simulation**: Convolve Bifrost/ART band-averaged maps with ALMA, BIMA beams (also rotated 90 deg) and compare statistics  
  > "additional degraded maps are calculated with the beam rotated by $90\,\deg$." (4.2 Dependence on angular resolution)
   - software: ART, Bifrost
   - fitting: _not stated_
   - validation: Compared simulated rms with observed  
  > "The simulated standard deviation, however, is roughly a factor two higher than the corresponding observational value." (4.2 Dependence on angular resolution)

## Software

- **SoAP** first version: Interferometric image reconstruction pipeline for solar ALMA data  
  > "constructed with the first version of the Solar ALMA Pipeline (SoAP)" (abstract)
- **CASA** : Basis of SoAP, CLEAN, TP dual-load calibration scripts  
  > "based on the Common Astronomy Software Applications (CASA[^2]) package" (2.2 Interferometric data processing)
- **ART** : Synthetic brightness temperature maps from Bifrost  
  > "calculated with the Advanced Radiative Transfer (ART) code" (4.2 Dependence on angular resolution)
- **Bifrost** : 3D radiation MHD simulation  
  > "3D radiation magnetohydrodynamic simulation with Bifrost" (4.2 Dependence on angular resolution)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean Tb, inner region (all) | 7400 | 453 (rms) | K | 3 | The corresponding average and standard deviation is $(7500 \pm 514)$ K for the whole FOV and $(7400 \pm 453)$ K for the inner region. |
| Mean Tb network / internetwork | 7588 / 7228 | not stated | K | 3 | / avg.            / 7400 / 7588 / 7228 / |
| Histogram FWHM network / internetwork | 782 / 702 | not stated | K | 3 | / histogram, FWHM /  752 /  782 /  702 / |
| Cross-correlation ALMA with AIA 304 and 131 | 0.38 | not stated | dimensionless | 4 | both reaching a moderate correlation of $\langle\mathcal{C}\rangle_t=0.38$ |
| Cross-correlation ALMA with AIA 171 | 0.33 | not stated | dimensionless | 4 | followed by SDO/AIA 17.1 nm with $\langle\mathcal{C}\rangle_t = 0.33$. |
| Simulated Tb rms with representative beam | 1033 (original 1549) | not stated | K | 5 | Using the representative beam from the ALMA observations presented here results in a standard deviation of 1033 K |
| Compact loop top Tb range | 8500 to 9650 | not stated | K | 3 | ALMA maps the hot loop tops at brightness temperatures between 8500 K and a maximum of 9650 K. |

## Qualitative findings

- Band 3 may receive contributions from a wider range of atmospheric heights than assumed; formation height needs study  
  > "might have contributions from a larger range of atmospheric heights than previously assumed" (abstract)

## Claim tuples

- H: Does ALMA Band 3 show network, internetwork and loop structure correlated with SDO channels? | E: Cross-correlate beam-matched SDO maps with ALMA maps | R: Best correlation with AIA 304 and 131 (0.38), then 171 (0.33) | F: Band 3 correlates best with AIA 171, 131 and 304 and shows weak imprints of large loops | **supported**
- H: Does limited angular resolution reduce Tb variance? | E: Convolve Bifrost maps with different beams | R: rms drops from 1549 K to 1033 K with the ALMA beam | F: Resolution strongly affects the distribution width; observed rms still about half the simulated | **supported**
- H: Are compact magnetic loops detectable in Band 3? | E: Examine ALMA maps against SDO | R: Loop tops 8000-9000 K, up to ~10 000 K | F: Loops appear optically thick and bright | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Self-calibration rejected as too aggressive for this dataset  
  > "self-calibration resulted in too aggressive corrections and loss of information on small spatial scales" (2.2 Interferometric data processing)
- How they decided it was enough: _not stated_
- Limitation (authors): Absolute Tb scale from TP remains uncertain  
  > "The absolute brightness temperature scale as set by Total Power measurements remains less certain and must be improved in the future." (abstract)
- Caveat (inferred, ours): Small FOV and single quiet region limit statistical generality
- Caveat (inferred, ours): Pointing errors required nonstandard processing that may bias small-scale structure
- Caveat (inferred, ours): Formation-height inference from correlations is qualitative
- Caveat (inferred, ours): SoAP not yet documented or released

## Reproducibility

- Data public (paper): Calibrated data downloaded from ALMA Archive  
  > "The calibrated ALMA data were downloaded from the ALMA Archive" (2.2 Interferometric data processing)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: SoAP code and parameters
- Missing: SDO alignment and mask thresholds
- Missing: ART/Bifrost simulation details
- Data volume (inferred): Large; hundreds of GB for interferometric solar time series plus TP maps
- Score (inferred): 3/5, Public data but processing depends on unreleased SoAP and unstated parameters; numeric results are clear.
- Rediscovery candidate: no, Recipe relies on the unpublished SoAP pipeline and unstated imaging parameters.

## Links

- Method: (cite: soap_inprep) (SoAP pipeline description)
- Method: (cite: 2017SoPh..292...88W) (TP calibration and Band 3 reference temperature)
- Companion: (cite: jafarzadeh_waves_inprep) (Oscillation analysis of the same data)
- Related: SolarALMA
- Related: SSALMON

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
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 41,
  "rate": 0.554
 },
 "evidence_ok": true
}
```
