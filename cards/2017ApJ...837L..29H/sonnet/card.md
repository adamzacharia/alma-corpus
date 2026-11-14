# An Extraordinary Outburst in the Massive Protostellar System NGC6334I-MM1: Quadrupling of the Millimeter Continuum

`2017ApJ...837L..29H` | The Astrophysical Journal Letters 2017 | first author: Hunter, T. R. | arXiv: 1701.08637 | DOI: 10.3847/2041-8213/aa5d0e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Has the millimeter continuum of the massive protostellar system NGC 6334I-MM1 changed between SMA (2008) and ALMA (2015-2016) epochs, and what does it imply for accretion and luminosity?  
  > "we perform a detailed comparison of ALMA images from 2015 and 2016 with SMA images obtained 7-8 years earlier, which reveals an extraordinary increase in the continuum emission from MM1" (1 Introduction)
- Target **NGC 6334I (MM1, MM2, MM3, MM4)**: coordinates _not stated_; z/distance 1.30±0.09 kpc  
  > "using the new maser parallax distance of 1.30$\pm$0.09 kpc for the neighboring source I(N)" (1 Introduction); distance from maser parallax of NGC 6334I(N) (Chibueze14; Reid14)  
  > "using the new maser parallax distance of 1.30$\pm$0.09 kpc for the neighboring source I(N)" (1 Introduction)

## Data provenance

- ALMA projects: 2015.A.00022.T, 2013.1.00600.S
- bands: ALMA Band 6 (1.3 mm, 2015), 1.1 mm and 0.87 mm (2016); SMA 1.3 and 0.87 mm (2008)  
  > "new ALMA Cycle 3 observations at 1.1 and 0.87 mm acquired in 2016 via Director’s Discretionary Time, along with older observations using the SMA in 2008 at 1.3 and 0.87 mm" (2.1 Millimeter and submillimeter interferometry)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: ALMA 0.28 GHz (1.1 mm), 0.38 GHz (0.87 mm); SMA 1.2 and 0.9 GHz  
  > "Continuum bandwidth (GHz) | 0.28 | 0.38 | 1.2 | 0.9" (Table 1)
- arrays: _not stated_
- configurations: ALMA C36-4, C36-5; SMA very extended  
  > "Configuration(s) | C36-4, C36-5 | C36-4, C36-5 | Very extended | Very extended" (Table 1)
- baselines: _not stated_
- angular resolution: 0.22x0.16 arcsec (1.1 mm), 0.21x0.16 arcsec (0.87 mm); SMA 0.84x0.33 and 0.49x0.25 arcsec  
  > "$0.22\times 0.16$ ($-82$) | $0.21\times 0.16$ ($-79$) | $0.84\times 0.33$ ($+16$) | $0.49 \times 0.25$ ($+9$)" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: rms 2, 3 mJy/beam (ALMA); 7, 20 mJy/beam (SMA)  
  > "RMS noise (mJy beam$^{-1}$)$^{a}$ | 2 | 3 | 7 | 20" (Table 1)
- time on source: ALMA 26+26 min (1.1 mm), 27+27 min (0.87 mm)  
  > "Time on Source (min) | 26, 26 | 27, 27 | 150, 211 | 226" (Table 1)
- observing dates: ALMA 2016 Jul-Aug; SMA 2008 Aug; earlier ALMA 2015 Aug 29  
  > "Observation date(s) | 2016 Jul 18, 2016 Aug 02 | 2016 Jul 17, 2016 Aug 02 | 2008 Aug 17,19 | 2008 Aug 11" (Table 1)
- pi or archival as stated: 2016 data via Director's Discretionary Time; 2015 Cycle 2 data from Brogan16  
  > "acquired in 2016 via Director’s Discretionary Time" (2.1 Millimeter and submillimeter interferometry)
- Other facility **SMA**: 2008 1.3 and 0.87 mm continuum images  
  > "older observations using the SMA in 2008 at 1.3 and 0.87 mm" (2.1 Millimeter and submillimeter interferometry)
- Other facility **HartRAO 26 m**: Long-term 22.2 GHz H2O and 6.7 GHz CH3OH maser monitoring  
  > "long-term maser monitoring program at the Hartebeesthoek Radio Observatory (HartRAO) using the 26 m telescope" (2.2 Single-dish maser monitoring)
- External data: 2015 Cycle 2 ALMA 1.3 mm image and parameters  
  > "Our earlier (Cycle 2) ALMA observations of this field at 1.3 mm are also used in this Letter." (2.1 Millimeter and submillimeter interferometry) [from (cite: Brogan16)]
- External data: Brightness-temperature luminosities of MM1 components, sum 42000±5000 Lsun  
  > "sum of the brightness temperature luminosity estimates for the five MM1 components affected (A, B, C, D, and G) reported by (cite: Brogan16), which is $42000\pm5000$ $L_\odot$" (3.3 Luminosity Increase) [from (cite: Brogan16)]
- External data: Td scales as 1/4 power of central luminosity  
  > "Radiative transfer models of dust envelopes surrounding outbursting protostars indicate that $T_d$ scales as the 1/4 power of the central luminosity" (3.3 Luminosity Increase) [from (cite: Taquet16; Johnstone13)]

## Processing

### Calibration

- pipeline or manual: ALMA: pipeline; SMA: MIRIAD calibration  
  > "The SMA data were calibrated in MIRIAD and imaged in CASA." (2.1 Millimeter and submillimeter interferometry)
- casa version: _not stated_
- pipeline version: C3R4B  
  > "The Cycle 3 ALMA data were calibrated using version C3R4B of the pipeline" (2.1 Millimeter and submillimeter interferometry)
- archive products used as is: _not stated_
- flux calibrator: J1733-1304 (ALMA); Callisto (SMA)  
  > "Flux calibrator | J1733-1304 | J1733-1304 | Callisto | Callisto" (Table 1)
- flux scale uncertainty: 5% ALMA, 10% SMA  
  > "The estimated flux scale uncertainties are 5% for ALMA and 10% for SMA." (2.1 Millimeter and submillimeter interferometry)
- self calibration: Continuum iteratively self-calibrated using bright emission as initial model  
  > "The continuum data were iteratively self-calibrated, using the bright emission as the initial model." (2.1 Millimeter and submillimeter interferometry)

### Imaging

- task: _not stated_
- deconvolver: Multi-scale clean, scales 0, 5, 15 pixels  
  > "Multi-scale clean was used on the ALMA data with scales of 0, 5, and 15 times the pixel size ($0.03''$)." (2.1 Millimeter and submillimeter interferometry)
- weighting robust: ALMA -0.5 (1.1 mm), +0.5 (0.87 mm); SMA 0.0  
  > "Robust clean parameter | $-0.5$ | +0.5 | 0.0 | 0.0" (Table 1)
- uv taper: _not stated_
- cell size: 0.03 arcsec  
  > "scales of 0, 5, and 15 times the pixel size ($0.03''$)" (2.1 Millimeter and submillimeter interferometry)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Followed Brogan16 procedure; <5% residual line contamination  
  > "We followed the procedure described in (cite: Brogan16) and estimate that the resulting images suffer $<5\%$ residual line contamination toward the hot cores." (2.1 Millimeter and submillimeter interferometry)
- primary beam correction: applied to all images  
  > "All images were corrected for primary beam attenuation." (2.1 Millimeter and submillimeter interferometry)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: see resolution  
  > "$0.22\times 0.16$ ($-82$) | $0.21\times 0.16$ ($-79$)" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Line-free channel selection procedure for continuum  
  > "We followed the procedure described in (cite: Brogan16)" (2.1 Millimeter and submillimeter interferometry) [from (cite: Brogan16)]
- 2015 Cycle 2 ALMA observations and processing  
  > "They are more fully described in (cite: Brogan16)" (2.1 Millimeter and submillimeter interferometry) [from (cite: Brogan16)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for each band
- Self-calibration solution intervals and number of iterations
- Clean masks, thresholds and image sizes
- SMA calibration details and MIRIAD-to-CASA steps
- CASA version
- Simobserve parameters (thermal noise, integration times)
- Aperture position for the brightness temperature measurement
- How uncertainty on the luminosity factor of 70±20 was propagated

## Analysis recipe

1. **Compare ALMA and SMA continuum flux of MM1**: Convolve 2015 ALMA 1.3 mm image to SMA resolution and compare flux densities  
  > "When we convolve the ALMA image to the resolution of the SMA image, the result (Fig. 1c) shows a significant difference in the morphology and the total flux density of MM1" (3.1 Millimeter continuum)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared other sources MM2-4 as constant controls  
  > "Interestingly, the other sources in the protocluster (MM2, MM3, and MM4) do not show significant differences." (3.1 Millimeter continuum)
2. **Exclude uv-sampling effects with simulated SMA observation**: simobserve of the ALMA image with SMA uv-coverage and flagging, scaled in frequency by a spectral index map from 1.1 and 0.87 mm ALMA images; subtract from actual SMA image  
  > "we simulated the 2008 SMA observations using the 2015 1.3 mm ALMA image (Fig 1a) as the sky model and applying the identical $uv$-coverage and flagging of our SMA observations" (3.1 Millimeter continuum)
   - software: CASA simobserve
   - parameter: spectral index averages MM1=2.9, MM2=3.2, MM4=2.4  
  > "average values: MM1=2.9, MM2=3.2, MM4=2.4" (3.1 Millimeter continuum)
   - fitting: _not stated_
   - validation: SMA would recover 87% of MM1 flux, so uv-sampling cannot explain the difference  
  > "We find that the SMA could have recovered $87\%$ (9.4 Jy) of the MM1 emission recovered by ALMA" (3.1 Millimeter continuum)
3. **Estimate luminosity increase from brightness temperature**: Measure TB increase in 1.3 arcsec aperture; Td proportional to TB; Td ∝ L^(1/4)  
  > "In an aperture of diameter $1.3''$ ($d=1700$ au), $T_B$ has increased by a factor of 2.9$\pm$0.3 (from 33 to 96 K)." (3.3 Luminosity Increase)
   - assumption: Central protostar in thick spherical dust shell; tau unchanged  
  > "we consider this change in the context of a simple model of a central protostar surrounded by a thick spherical shell of dust" (3.3 Luminosity Increase)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : SMA imaging, ALMA imaging, simobserve  
  > "The SMA data were calibrated in MIRIAD and imaged in CASA." (2.1 Millimeter and submillimeter interferometry)
- **MIRIAD** : SMA calibration  
  > "The SMA data were calibrated in MIRIAD and imaged in CASA." (2.1 Millimeter and submillimeter interferometry)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| MM1 flux increase factor, 1.3 mm | 3.9 | 0.6 | dimensionless | 2 | We conclude that MM1 has flared by a factor of 3.9$\pm$0.6 at 1.3 mm |
| MM1 flux increase factor, 0.87 mm | 4.2 | 0.5 | dimensionless | 2 | yielding a comparable increase factor of 4.2$\pm$0.5 |
| Mean MM1 increase factor | 4.0 | 0.3 | dimensionless | 2 | Combining the two bands, the mean factor is 4.0$\pm$0.3 |
| MM1 1.3 mm flux density, ALMA vs SMA | 10.8 vs 2.34 | 0.9, 0.22 | Jy | 1 | (10.8$\pm$0.9 vs. 2.34$\pm$0.22 Jy) |
| MM1 0.87 mm flux density, SMA 2008 to ALMA 2016 | 6.65 to 33.3 | 0.68, 1.7 | Jy | 2 | yields an increase in the flux density of MM1 from 6.65$\pm$0.68 to 33.3$\pm$1.7 Jy |
| Excess at 1.3 mm | 6.9 | 0.8 | Jy | 2 | $f_{\rm
  exc}=6.9\pm0.8$ Jy |
| Brightness temperature increase | 2.9 (33 to 96 K) | 0.3 | dimensionless | 3 | $T_B$ has increased by a factor of 2.9$\pm$0.3 (from 33 to 96 K) |
| Luminosity increase factor | 70 | 20 | dimensionless | 3 | we compute a luminosity increase factor of $l_{\rm inc}=70\pm20$ |
| Pre-outburst luminosity | 590 | 170 | Lsun | 3 | the pre-outburst luminosity is then $590\pm170$ $L_\odot$ |
| Total energy released | 0.8e46 | not stated | erg | 3 | the total energy released (so far) is $0.8\times10^{46}$ erg |

## Qualitative findings

- Excess emission centered on HC HII region MM1B, elongated perpendicular to the outflow, possibly a fragmented disk  
  > "the position angle of the elongated MM1 excess emission is exactly perpendicular to the large-scale bipolar outflow" (4 Discussion)

## Claim tuples

- H: Did MM1 dust continuum brighten between 2008 and 2015/2016? | E: Compare SMA 2008 with ALMA 2015/2016 images, with simulated SMA observations of the ALMA image | R: Flux increased by 4.0±0.3 while MM2-4 stayed constant | F: MM1 underwent a real continuum outburst, not due to uv-sampling or line contamination | **supported**
- H: Is the continuum flare linked to maser flaring? | E: HartRAO monitoring of H2O and CH3OH masers | R: Masers increased by a factor of 10 by mid-May 2015, H2O by 40 versus 2011 | F: An energetic accretion event began in early 2015 | **supported**
- H: How large is the luminosity surge? | E: Scale Td change from brightness temperature increase with L^(1/4) | R: Luminosity increase factor 70±20 | F: Consistent with the largest accretion bursts in Meyer17 simulations | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Simulated SMA observation to exclude uv-sampling differences  
  > "To exclude $uv$-sampling effects as the culprit, we simulated the 2008 SMA observations" (3.1 Millimeter continuum)
- Alternative: Line contamination ruled out since MM2 is similarly line-rich but unchanged  
  > "the spectrum of the MM2 hot core is similarly line-rich (cite: Zernickel12) so a line contamination effect should manifest in that source as well" (3.1 Millimeter continuum)
- How they decided it was enough: _not stated_
- Limitation (authors): Brightening factor may have evolved between 2015 and 2016; geometry uncertain  
  > "however, the brightening factor could have evolved over 2015-2016" (3.1 Millimeter continuum)
- Caveat (inferred, ours): Luminosity scaling assumes Td ∝ L^1/4 and unchanged optical depth, from low-mass models
- Caveat (inferred, ours): Different epochs and tunings; spectral index correction is approximate
- Caveat (inferred, ours): Only two continuum epochs, so rise time is poorly constrained

## Reproducibility

- Data public (paper): ALMA data listed with project codes in acknowledgments  
  > "This Letter makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00600.S, 2015.A.00022.T." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Line-free channel ranges
- Missing: Self-calibration parameters
- Missing: SMA data calibration details
- Missing: HartRAO maser data (MacLeod in preparation)
- Data volume (inferred): ~100-300 GB for ALMA data; SMA data small
- Score (inferred): 3/5, ALMA data public and key numbers given, but processing details are deferred to earlier work and SMA data details are sparse.
- Rediscovery candidate: no, Key imaging and self-calibration details and SMA data processing are not fully specified.

## Links

- Method: (cite: Brogan16) (Continuum line-free channel procedure and 2015 ALMA data)
- Companion: (cite: Brogan16) (Earlier ALMA 1.3 mm study of NGC 6334I)
- Related: HartRAO maser monitoring program

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 43,
  "rate": 0.652
 },
 "evidence_ok": true
}
```
