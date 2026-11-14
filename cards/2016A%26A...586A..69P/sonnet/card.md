# The radio continuum spectrum of Mira A and Mira B up to submillimeter wavelengths

`2016A&A...586A..69P` | Astronomy and Astrophysics 2016 | first author: Planesas, P. | arXiv: 1512.08638 | DOI: 10.1051/0004-6361/201527833

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, stellar_physics
- Question: What is the origin of the cm-to-submm continuum emission of Mira A and Mira B, and does the relative position of the pair agree with the preliminary orbit?  
  > "to better constrain the origin of the continuum emission of the Mira AB binary system and to check its orbit." (abstract)
- Target **Mira AB (o Ceti)**: coordinates _not stated_; z/distance 110 pc  
  > "In this paper, we adopt a distance to Mira of 110 pc." (Introduction); distance from adopted; compared with period-luminosity relations and Hipparcos parallax  
  > "In this paper, we adopt a distance to Mira of 110 pc." (Introduction)

## Data provenance

- ALMA projects: 2012.1.00047.S, 2013.1.00047.S
- bands: Band 9 (679 GHz), Band 7 (338 GHz); SV Bands 6 and 3  
  > "We performed ALMA radio continuum observations of the Mira system in band 9 at 679.0 GHz on 2014 June 16" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: Band 9: 7.95 GHz, four 2 GHz basebands; Band 7: two 2 GHz basebands at 332.0 and 344.6 GHz  
  > "The continuum bandwidth was 7.95 GHz wide, composed of four 2 GHz wide contiguous basebands." (Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: up to 650 m (bands 7 and 9)  
  > "using an array configuration of 34 antennas with baselines up to 650 m" (Observations)
- angular resolution: Band 9 0.21''x0.15''; Band 7 0.32''x0.30''  
  > "The angular resolution was $0.32\ensuremath{''}\times0.30\ensuremath{''}$." (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Band 9: 219 s integration  
  > "which is an order of magnitude higher than expected for a 219-second integration time" (Data reduction)
- observing dates: Band 9 2014 June 16; Band 7 2014 June 12, 14, 15; SV bands 3 and 6 Oct-Nov 2014  
  > "ALMA radio continuum observations in band 7 at 338.3 GHz were performed on 2014 June 12, 14, and 15" (Observations)
- pi or archival as stated: _not stated_
- Other facility **HST**: Archival data (projects 10091 and 11224) re-analysed for relative positions  
  > "our own analysis of additional HST archival data (HST projects 10091 and 11224)" (Relative positions of the binary system)
- Other facility **ALMA Science Verification (bands 3, 6)**: Images from ALMA Partnership used for fluxes and positions  
  > "we have obtained the flux density from the images provided by the ALMA Partnership" (Data reduction)
- External data: VLA 8.5 and 22.5 GHz fluxes of Mira A and B  
  > "the weighted average of measurements made at 8.5 and 22.5 GHz by (cite: matthews2006)" (The shape and origin of the continuum spectra) [from (cite: matthews2006)]
- External data: Mira A 43.1 GHz flux  
  > "the Mira A measurements at 43.1 GHz by (cite: reid2007)" (The shape and origin of the continuum spectra) [from (cite: reid2007)]
- External data: Preliminary orbit parameters  
  > "The latest orbit parameters can at best be considered preliminary (cite: prieur2002)." (Introduction) [from (cite: prieur2002)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: SV band 3/6 images used without recalibration  
  > "We have not calibrated the band 6 and band 3 data obtained in the Science Verification campaign again" (Data reduction)
- flux calibrator: Band 9: J2258-279 at 0.217 Jy, scale from Uranus  
  > "Flux density calibration was performed with the quasar J2258-279, assuming a flux density of 0.217 Jy." (Observations)
- flux scale uncertainty: ~20% band 9; ~7% band 7  
  > "we assume a conservative accuracy of $\sim$20% for the absolute flux scale." (Observations)
- self calibration: Applied on strong continuum source in bands 9 and 7  
  > "The self-calibration on the strong continuum source reduced the noise to 1.9 mJy beam$^{-1}$" (Data reduction)

### Imaging

- task: CASA cleaning  
  > "The data processing was performed with the CASA package and we used a Briggs robust value of 0.5 for cleaning." (Data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "we used a Briggs robust value of 0.5 for cleaning" (Data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Only line-free channels cleaned, end channels excluded  
  > "We cleaned the maps corresponding to the channels free of line emission and also excluded the end channels of each spectral window." (Data reduction)
- primary beam correction: Applied to final band 9 image  
  > "after the primary beam correction was applied to produce the final image" (Data reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Band 9 0.213''x0.149'' PA 56.9; Band 7 0.316''x0.304'' PA 37.9  
  > "The fitted beam used in restoration was $0.316\ensuremath{''}\times0.304\ensuremath{''}$ at PA $= 37.9\ensuremath{^\circ}$." (Data reduction)
- final rms: Band 9 1.9 mJy/beam; Band 7 0.20 mJy/beam  
  > "The final image noise was 0.20 mJy beam$^{-1}$ (SNR $>1500$)." (Data reduction)

### Inherited from earlier work

- Band 3/6 SV data calibration and images  
  > "these data have been carefully calibrated by other authors" (Data reduction) [from (cite: matthews2015); (cite: vlemmings2015); (cite: alma2015)]
- Flux scale extrapolation to band 9  
  > "following the standard procedure described in the ALMA Technical Handbook" (Observations) [from ALMA Technical Handbook]

### Not stated but needed to reproduce (our reading)

- CASA version
- Self-calibration solution intervals and number of iterations
- Line-free channel list
- Image size and cell size
- Clean masks and thresholds
- Fitting method and weighting for spectral-index power-law fits
- Which band 7 date/dataset gave the quoted fluxes
- HST analysis procedure

## Analysis recipe

1. **Image continuum**: Clean line-free channels, self-calibrate, primary-beam correct  
  > "We only cleaned the line free channels, excluded the end channels of each spectral window, applied self-calibration, and cleaned with a Briggs robust value of 0.5." (Data reduction)
   - software: CASA
   - parameter: Briggs robust 0.5  
  > "cleaned with a Briggs robust value of 0.5" (Data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure fluxes and positions**: Simultaneous 2D Gaussian fit of A and B; also polygon total flux  
  > "We performed a simultaneous two-dimensional Gaussian fit to determine the flux and size of each source." (Data reduction)
   - fitting: 2D Gaussian; errors are formal fit errors  
  > "The quoted value for the flux uncertainty is the formal error in the Gaussian fit" (Data reduction)
   - validation: Gaussian and polygon fluxes agree  
  > "The values obtained with two methods (Gaussian fit, and total flux within a polygon surrounding the emitting area) agree in all bands." (Data reduction)
3. **Fit spectral indices**: Power-law fits to ALMA plus literature VLA fluxes; two-component for Mira B  
  > "The black line is the fit to all the Mira A measurements, which is well represented by a power law with a spectral index of $\alpha=1.98\pm0.04$." (The shape and origin of the continuum spectra)
   - assumption: Optically thick thermal emission, Te 1e4 K, distance 110 pc  
  > "optically thick emission ($\nu^2$ law) and a typical electron temperature of $10^4$ K" (The shape and origin of the continuum spectra)
   - fitting: _not stated_
   - validation: Tested 20% lower band 9 flux changes index to 1.96  
  > "would barely reduce the spectral index to $\alpha=1.96\pm0.04$" (The shape and origin of the continuum spectra)
4. **Relative astrometry vs orbit**: Gaussian-fit centroid offsets of B relative to A compared with preliminary orbit  
  > "The HST results lie close to the preliminary orbit, but this is not the case for the ALMA results, which clearly lie significantly apart by $\sim$0.014$''$." (Relative positions of the binary system)
   - fitting: Linear fit to ALMA positions  
  > "This fit is a straight line, representing a very short arc of the orbit" (Relative positions of the binary system)
   - validation: Agrees with Vlemmings and JVLA results  
  > "Our results for the ALMA bands 3 and 6 Science Verification data agree with the independent analysis made by (cite: vlemmings2015)" (Relative positions of the binary system)

## Software

- **CASA** : Data processing and cleaning  
  > "The data processing was performed with the CASA package" (Data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mira A spectral index | 1.98 | 0.04 | dimensionless | 3 | The Mira A continuum emission has a spectral index of $1.98\pm0.04$ |
| Mira B spectral index, high frequency | 1.93 | 0.06 | dimensionless | 3 | The spectral index of the Mira B continuum emission is $1.93\pm0.06$ |
| Mira B spectral index, below ~95 GHz | 1.22 | 0.09 | dimensionless | 3 | a shallower spectral index of $1.22\pm0.09$ at longer wavelengths |
| Band 9 flux Mira A | 1460.8 | 0.5 | mJy | 2 | The total flux is $1460.8\pm0.5$ mJy for Mira A and $124.8\pm0.5$ mJy for Mira B. |
| Band 9 flux Mira B | 124.8 | 0.5 | mJy | 2 | The total flux is $1460.8\pm0.5$ mJy for Mira A and $124.8\pm0.5$ mJy for Mira B. |
| Band 7 flux Mira B | 25.5 | 0.2 | mJy | 2 | $25.5\pm0.2$ mJy for Mira B |
| Offset from preliminary orbit | ~0.014 | not stated | arcsec | 4 | we have found a significant discrepancy, of the order of 0.014$''$, between the ALMA measurements and the predicted orbit. |
| Mira B emitting region size (Gaussian HWHM-power size) | 0.019 arcsec = 3.1e13 cm | not stated | arcsec | 3 | we derive a half power angular size of a Gaussian distribution of $0.019\ensuremath{''}$, which corresponds to 3.1 $10^{13}$ cm at a distance of 110 pc. |

## Qualitative findings


## Claim tuples

- H: Mira A submm continuum comes from a radio photosphere | E: Fit power law across 8-700 GHz | R: alpha=1.98±0.04 | F: Consistent with radio photosphere models | **supported**
- H: Mira B is a single ionized component | E: Fit B spectrum | R: alpha 1.22 below 95 GHz, 1.93 above | F: Needs two components | **refuted**
- H: ALMA positions agree with the preliminary orbit | E: Gaussian centroid separations | R: ~14 mas offset | F: Orbit needs improvement | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Absolute flux scale uncertainty ~20% in band 9; resolved stellar disks may offset centroids  
  > "some modeling may be required to determine the geometrical center of the disks" (Conclusions)
- Caveat (inferred, ours): Centroid offsets may be affected by hotspot structure
- Caveat (inferred, ours): Spectral fits mix non-simultaneous epochs and stellar phase
- Caveat (inferred, ours): Disagreement with Ramstedt fluxes unresolved

## Reproducibility

- Data public (paper): ALMA data cited via ADS/JAO code; SV data public  
  > "This paper makes use of the following ALMA data: ADS/ JAO.ALMA#2013.1.00047.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and scripts
- Missing: self-cal parameters
- Missing: fitting details
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and simple recipe, but missing imaging and fitting details.
- Rediscovery candidate: yes, Public data, numeric fluxes and spectral indices from simple imaging and Gaussian fits.

## Links

- Companion: (cite: matthews2015) (Independent analysis of SV data)
- Companion: (cite: vlemmings2015) (Independent analysis of SV data)
- Related: ALMA Science Verification long baseline campaign

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2012.1.00047.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 40,
  "rate": 0.606
 },
 "evidence_ok": true
}
```
