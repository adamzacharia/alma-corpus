# ALMA Band 8 Continuum Emission from Orion Source I

`2016ApJ...833..238H` | The Astrophysical Journal 2016 | first author: Hirota, Tomoya | arXiv: 1611.00855 | DOI: 10.3847/1538-4357/833/2/238

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What are the band 8 continuum flux densities, size and brightness temperature of Orion Source I, and do they support optically thick thermal dust emission from an edge-on disk?  
  > "The present newer and higher resolution data could put better constraints on the width of the minor axis, and establish an improved lower limit on the brightness temperature." (1 Introduction)
- Target **Orion Source I**: coordinates RA(J2000)=05h35m14.512s, Dec(J2000)=-05d22'30.57" (tracking center)  
  > "The tracking center position was RA(J2000)=05h35m14.512s, Decl(J2000)=-05d22’30.57"." (Observations and Data Analysis); "at a distance of 420 pc from the Sun (cite: menten2007; kim2008)" (Introduction); z/distance 420 pc  
  > "The tracking center position was RA(J2000)=05h35m14.512s, Decl(J2000)=-05d22’30.57"." (Observations and Data Analysis); "at a distance of 420 pc from the Sun (cite: menten2007; kim2008)" (Introduction); distance from Menten et al. 2007; Kim et al. 2008  
  > "The tracking center position was RA(J2000)=05h35m14.512s, Decl(J2000)=-05d22’30.57"." (Observations and Data Analysis); "at a distance of 420 pc from the Sun (cite: menten2007; kim2008)" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00048.S
- bands: Band 8 (430, 460, 490 GHz)  
  > "we present the new continuum measurement results with ALMA at band 8 (430 GHz, 460 GHz, and 490 GHz)" (Introduction)
- frequencies and spectral setup: Four spectral windows, two of 1875 MHz and two of 937.5 MHz; channel spacings 976.562 kHz and 488.281 kHz  
  > "The ALMA correlator provided the four spectral windows with the total bandwidth of 1875 MHz and 937.5 MHz for two windows each." (Observations and Data Analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Longest baseline 2270, 1574, 1466 m; only uv > 400 kλ used  
  > "| 430 | Sep. 22 | 5625 | 35 | 2270 | 1929 | 1200 | 83$\times$67 | $-$79.8 | 2.7 |" (Table 1)
- angular resolution: ~100 mas (40 au)  
  > "The procedure provides an angular resolution of $\sim$100 mas, corresponding to the linear resolution of 40 au at the distance to Orion KL." (Observations and Data Analysis)
- max recoverable scale: _not stated_
- sensitivity: rms 2.7, 4.1, 3.8 mJy/beam (430, 460, 490 GHz)  
  > "| 490 | Jul. 27 | 4688 | 41 | 1466 | 315 | 400 | 111$\times$79 | 84.5 | 3.8 |" (Table 1)
- time on source: 1929 s (430), 410 s (460), 315 s (490)  
  > "| 430 | Sep. 22 | 5625 | 35 | 2270 | 1929 | 1200 | 83$\times$67 | $-$79.8 | 2.7 |" (Table 1)
- observing dates: 2015: Sep 22 (430 GHz), Aug 27 (460 GHz), Jul 27 (490 GHz)  
  > "| 460 | Aug. 27 | 5625 | 40 | 1574 | 410 | 430 | 104$\times$87 | 82.9 | 4.1 |" (Table 1)
- pi or archival as stated: _not stated_
- External data: Previously published continuum flux densities used in the SED (6 to 660 GHz)  
  > "The flux densities are plotted in Figure [2](#fig-sed) along with previous observations (cite: plambeck2013; hirota2015; plambeck2016)." (Results and discussion) [from (cite: plambeck2013; hirota2015; plambeck2016)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Used calibrated data delivered by EA-ARC  
  > "We employed the calibrated data delivered by the East-Asia ALMA Regional Center (EA-ARC)." (Observations and Data Analysis)
- flux calibrator: J0423-013 (flux); J0522-3627 (bandpass)  
  > "A primary flux calibrator and band-pass calibrator were J0423-013, and J0522-3627, respectively." (Observations and Data Analysis)
- flux scale uncertainty: _not stated_
- self calibration: Phase and amplitude self-cal on Source I continuum using clean and gaincal  
  > "both phase and amplitude self-calibration was done with the continuum emission of Source I by integrating over all the channels using CASA tasks `clean` and `gaincal`." (Observations and Data Analysis)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: Only uv distance > 400 kλ used to resolve out extended emission  
  > "we employed the visibility data with the UV distance longer than 400 k$\lambda$ to resolve out extended emission components" (Observations and Data Analysis)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub with line-free channels  
  > "visibility data were separated into spectral lines and continuum emissions by setting the line free channels with the CASA task `uvcontsub`." (Observations and Data Analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 83×67, 104×87, 111×79 mas (430, 460, 490 GHz)  
  > "| 460 | Aug. 27 | 5625 | 40 | 1574 | 410 | 430 | 104$\times$87 | 82.9 | 4.1 |" (Table 1)
- final rms: 2.7, 4.1, 3.8 mJy/beam  
  > "| 430 | Sep. 22 | 5625 | 35 | 2270 | 1929 | 1200 | 83$\times$67 | $-$79.8 | 2.7 |" (Table 1)

### Inherited from earlier work

- uv > 400 kλ cut to resolve out extended emission  
  > "we employed the visibility data with the UV distance longer than 400 k$\lambda$ to resolve out extended emission components (cite: hirota2015)" (Observations and Data Analysis) [from (cite: hirota2015)]
- SED fitting procedure  
  > "The same fitting procedures are applied to the present data as described in (cite: hirota2015)." (Results and discussion) [from (cite: hirota2015)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Line-free channel ranges
- Clean parameters (weighting, robust, cell, image size, mask, niter)
- Self-calibration solution intervals
- Which uv weighting was used for the real images (uniform only stated for simulation)
- Absolute flux scale uncertainty and the flux calibrator model
- Exact flux densities and uncertainties of the literature points in the SED
- Fitting method/weights for the power-law SED
- Brightness temperature formula
- How the 490 GHz spectral windows were selected

## Analysis recipe

1. **Separate continuum and self-calibrate**: uvcontsub with line-free channels, then phase and amplitude self-calibration on the continuum  
  > "both phase and amplitude self-calibration was done with the continuum emission of Source I by integrating over all the channels using CASA tasks `clean` and `gaincal`." (Observations and Data Analysis)
   - software: CASA
   - parameter: Only three of four spectral windows used at 490 GHz because of calibration problems near 487 GHz  
  > "we used only three spectral windows among four ALMA basebands to make a continuum image at 490 GHz." (Observations and Data Analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **Image continuum at long baselines**: Imaging with uv > 400 kλ; maps registered on continuum peak because of astrometric offsets  
  > "Thus, all the maps are registered based on the continuum peak positions" (Observations and Data Analysis)
   - software: CASA
   - parameter: uv distance > 400 kλ  
  > "we employed the visibility data with the UV distance longer than 400 k$\lambda$" (Observations and Data Analysis)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure source size, flux and Tb**: Two-dimensional Gaussian fit to the images; brightness temperature from the marginally resolved size  
  > "The source properties are determined by fitting the two dimensional Gaussian to the images and the derived parameters are listed in Table [2](#tab-cont)." (Results and discussion)
   - software: CASA
   - assumption: Distance 420 pc  
  > "at a distance of 420 pc from the Sun (cite: menten2007; kim2008)" (Introduction)
   - fitting: _not stated_
   - validation: Simulated Gaussian of 220×50 mas, 1 Jy, with simobserve at the 460 GHz uv coverage recovered flux and size  
  > "the derived flux density and deconvolved source size, 0.9996 Jy and 220.0 mas$\times$49.8 mas can reconstruct the model parameters." (Results and discussion)
4. **Fit SED power law**: Power-law F=p ν^q fit to flux densities from 6 to 660 GHz; highest-resolution point per band; only the 460 GHz point of this work used  
  > "we only use the 460 GHz data and do not include the 430 GHz and 490 GHz data in order not to put too much weight for our band 8 data in the fitting." (Results and discussion)
   - fitting: Procedure as in Hirota et al. 2015; details not stated  
  > "The same fitting procedures are applied to the present data as described in (cite: hirota2015)." (Results and discussion)
   - validation: _not stated_

## Software

- **CASA** : Calibration, imaging, uvcontsub, self-calibration  
  > "The data were calibrated and imaged with the Common Astronomy Software Applications (CASA) package." (Observations and Data Analysis)
- **simobserve** : Simulating observations of a Gaussian source to test recovery  
  > "Using the CASA task `simobserve`, we simulated the ALMA imaging of a Gaussian source model" (Results and discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Deconvolved size | 220 mas × 50 mas (90 au × 20 au) | not stated | mas | 3 | The deconvolved size is 220 mas$\times$50 mas, corresponding to 90 au$\times$20 au at the distance of Orion KL. |
| Integrated flux density at 460 GHz | 1547 | 14 (fit error) | mJy | 3 | / 460 / 31.7(5) / $-$109.7(6) / 238.8(16)$\times$112.6(8) / 141.3(3) / 220.4(18)$\times$52.3(18) / 143.1(4) / 520(4) / 1547(14) / 777(7) / |
| Integrated flux density at 440 GHz | 1338 | 11 (fit error) | mJy | 3 | / 440 / 78.5(5) / $-$21.5(5) / 229.6(16)$\times$91.4(6) / 141.4(3) / 216.7(16)$\times$53.0(12) / 143.1(3) / 353(2) / 1338(11) / 735(6) / |
| Integrated flux density at 490 GHz | 1709 | 12 (fit error) | mJy | 3 | / 490 / 31.0(4) / $-$64.0(5) / 236.7(13)$\times$113.9(6) / 138.8(3) / 218.9(15)$\times$50.9(17) / 142.4(3) / 557(3) / 1709(12) / 756(6) / |
| Brightness temperature | 735, 777, 756 K at 440, 460, 490 GHz (700-800 K) | 6-7 K (fit) | K | 3 | The brightness temperature of 700-800 K is slightly higher than that derived from the 350 GHz and 660 GHz continuum data of 500 K |
| SED spectral index, 6-660 GHz | 1.86 | 0.05 | dimensionless | 4 | has an spectral index $q$ of 1.86$\pm$0.05 |
| SED spectral index, 230-660 GHz | 2.16 | 0.06 | dimensionless | 4 | gives the power-law index of 2.16$\pm$0.06 |
| Simulated recovery test | 0.9996 Jy, 220.0 × 49.8 mas | not stated | Jy | 3 | 0.9996 Jy and 220.0 mas$\times$49.8 mas can reconstruct the model parameters |

## Qualitative findings

- Continuum is elongated NW-SE, perpendicular to the low-velocity bipolar outflow  
  > "The structure is elongated along the NW-SE direction, which is perpendicular to the low-velocity NE-SW bipolar outflow." (Results and discussion)
- No clear SED turnover is seen  
  > "We cannot see a clear signature of a turnover in the SED" (Results and discussion)

## Claim tuples

- H: Band 8 continuum size is consistent with earlier millimeter/submillimeter measurements | E: 2D Gaussian fits to uv>400 kλ images at three frequencies | R: Deconvolved size 220×50 mas (90×20 au) | F: Consistent with previous ALMA results of Plambeck & Wright 2016 | **supported**
- H: The SED is optically thick thermal emission | E: Power-law SED fits including the new 460 GHz point | R: Index 1.86±0.05 (6-660 GHz), 2.16±0.06 (230-660 GHz); Tb 700-800 K | F: Consistent with optically thick black-body, thermal dust from an edge-on disk | **partially**
- H: H- free-free emission can be excluded | E: Compare Tb with VLA 1600 K | R: If the beam filling factor is smaller by a factor of two, Tb exceeds 1600 K | F: H- free-free cannot be fully ruled out if the source has unresolved structure | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Long-baseline cut to resolve out extended emission  
  > "we employed the visibility data with the UV distance longer than 400 k$\lambda$ to resolve out extended emission components" (Observations and Data Analysis)
- Alternative: Proton-electron and H- free-free opacity disfavored by Plambeck & Wright 2016  
  > "The optically thick H$^{-}$ free-free radiation is also ruled out since unrealistically high density or large disk mass is necessary" (Results and discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Astrometric offsets between frequencies; absolute positions not discussed  
  > "It is probably due to astrometric calibration errors in the ALMA observations/data analysis." (Observations and Data Analysis)
- Limitation (authors): Unresolved smaller-scale structure could have higher brightness temperature  
  > "there may be a smaller scale structure unresolved with the ALMA beam $\sim$40 au which could have a higher brightness temperature." (Results and discussion)
- Caveat (inferred, ours): Flux scale uncertainty not propagated to SED fit or Tb
- Caveat (inferred, ours): Only the 460 GHz point used in the SED; selection arbitrary
- Caveat (inferred, ours): Different epochs and variability not discussed
- Caveat (inferred, ours): Tb uncertainties are only fit errors

## Reproducibility

- Data public (paper): Project 2013.1.00048.S cited via ADS/JAO.ALMA  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00048.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and clean parameters
- Missing: Line-free channels
- Missing: Self-cal intervals
- Missing: Literature flux table
- Missing: SED fit details
- Data volume (inferred): ~100-300 GB raw for three band 8 executions
- Score (inferred): 3/5, Public data and simple Gaussian fits, but imaging, self-cal and SED fitting parameters are largely unstated.
- Rediscovery candidate: no, Key imaging and SED-fit settings are missing and the SED needs literature values that are not tabulated.

## Links

- Method: (cite: hirota2015) (uv cut and SED fitting procedure)
- Companion: (cite: plambeck2016) (Latest ALMA results at 350 and 660 GHz that this work compares with)

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 39,
  "rate": 0.574
 },
 "evidence_ok": true
}
```
