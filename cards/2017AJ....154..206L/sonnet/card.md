# Mapping Vinyl Cyanide and Other Nitriles in Titan's Atmosphere Using ALMA

`2017AJ....154..206L` | The Astronomical Journal 2017 | first author: Lai, J. C.-Y. | arXiv: 1710.06411 | DOI: 10.3847/1538-3881/aa8eef

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: solar_system, astrochemistry
- Question: Can C2H3CN be detected at submillimeter frequencies in Titan's atmosphere and spatially mapped, along with other nitriles, to constrain abundances and photochemistry/circulation?  
  > "These new, high-resolution detections have allowed for the first spatial distribution mapping of C$_2$H$_3$CN on Titan." (abstract)
- Target **Titan**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00033.S
- bands: Band 7, 335.3-349.2 GHz  
  > "using the band 7 receiver, covering frequencies in the range 335.3-349.2 GHz." (Observations)
- frequencies and spectral setup: single spectral window, 3840 channels, 488 kHz spacing, 976 kHz resolution after Hanning smoothing  
  > "containing 3840 channels and with a channel spacing of 488 kHz which (after Hanning smoothing by the correlator) corresponds to a spectral resolution of 976 kHz." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 39 antennas, baselines 15-349 m  
  > "Observations were made with 39 antennas in the telescope array, which provided baselines in the range 15-349 m" (Observations)
- baselines: _not stated_
- angular resolution: 1.22'' x 0.62''  
  > "the spatial resolution (FWHM of the Gaussian restoring beam) was $1.22''\times0.62''$." (Observations)
- max recoverable scale: _not stated_
- sensitivity: threshold 18 mJy, twice the continuum-subtracted RMS  
  > "a threshold flux level of 18 mJy (twice the RMS noise level of the continuum-subtracted line-free data)" (Observations)
- time on source: single 3-minute integration  
  > "A single 3-minute integration of Titan was obtained at UT 09:19" (Observations)
- observing dates: 2015 April 29  
  > "on 2015 April 29." (Observations)
- pi or archival as stated: _not stated_
- Line: C2H3CN 38_{1,38}-37_{1,37} (347.232 GHz)
- Line: C2H3CN 38_{0,38}-37_{0,37} (347.434 GHz)
- Line: C2H3CN 36_{2,34}-35_{2,33} (347.759 GHz)
- Line: C3H8 23_{0,23}-22_{1,22} (347.436 GHz)
- Line: CH3CN 19_9-18_9 (348.911 GHz)
- Other facility **Cassini CIRS**: CH4 limb-sounding temperatures (T102, T105, T110, T111 flybys) for temperature profile  
  > "Cassini CIRS CH$_4$ limb-sounding data obtained during the T102, T105, T110, and T111 Titan flybys" (Results)
- Other facility **HASI (Huygens)**: temperature profile 0-150 km  
  > "combined with the HASI profile (covering $z=0$-150 km)" (Results)
- External data: CO abundance 5.06e-5  
  > "the CO abundance was set to the more recent value of $5.06\times10^{-5}$ from (cite: ser16)." (Results) [from Serigano et al. 2016 (cite: ser16)]
- External data: C3H8 abundance 4.2e-7 above precipitation altitude, from CIRS  
  > "modeled using a constant C$_3$H$_8$ abundance of $4.2\times10^{-7}$ above the precipitation altitude as retrieved from CIRS observations by (cite: nix09)." (Results) [from Nixon et al. 2009 (cite: nix09)]
- External data: HC3N pressure broadening from HITRAN  
  > "were used for HC$_3$N (taken from the HITRAN catalog; (cite: gor17))." (Results) [from Gordon et al. 2017 (cite: gor17)]

## Processing

### Calibration

- pipeline or manual: standard JAO scripts  
  > "using the standard scripts provided by the Joint ALMA Observatory, as described by (cite: cor15)." (Observations)
- casa version: CASA 4.5.3  
  > "processed in the NRAO CASA software (version 4.5.3)" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Butler-JPL-Horizons 2012 Titan flux model  
  > "scaled to match the Butler-JPL-Horizons 2012 Titan flux model." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: clean  
  > "Imaging and deconvolution were performed using the `clean` task" (Observations)
- deconvolver: Hogbom  
  > "the point-spread function was deconvolved using the Hogbom algorithm" (Observations)
- weighting robust: natural  
  > "with natural visibility weighting" (Observations)
- uv taper: _not stated_
- cell size: 0.1'' x 0.1''  
  > "The image pixel size was set to $0.1''\times0.1''$" (Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub  
  > "the continuum was subtracted from the visibility amplitudes using the CASA `uvcontsub` task." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.22'' x 0.62''  
  > "was $1.22''\times0.62''$." (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Calibration processing as described in earlier work  
  > "using the standard scripts provided by the Joint ALMA Observatory, as described by (cite: cor15)." (Observations) [from (cite: cor15)]
- Radiative transfer modeling methodology  
  > "Following the methodology of (cite: cor14; cor15), the observed spectrum was modeled using the line-by-line radiative transfer module of the NEMESIS atmospheric retrieval code" (Results) [from (cite: cor14; cor15)]
- Step model profiles for C2H3CN and C2H5CN  
  > "A step model (with a constant value above 300 km and zero below) was adopted for the C$_2$H$_3$CN and C$_2$H$_5$CN vertical abundance profiles (after (cite: cor15; pal17))" (Results) [from (cite: cor15; pal17)]
- CIRS temperature retrieval method  
  > "retrieved following the same methodology as (cite: ach08)." (Results) [from (cite: ach08)]
- N2, CH4, CO isotopologue abundances  
  > "The abundances of nitrogen, methane, and carbon monoxide isotopologues were the same as those used by (cite: tea13)." (Results) [from (cite: tea13)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum subtraction
- Velocity integration ranges for moment maps
- Contour factor n and per-map RMS values
- Exact CIRS temperature profile data
- Initial values and optimizer settings for NEMESIS fits
- Number of iterations/clean mask
- Spectral windows and calibrators other than flux scale

## Analysis recipe

1. **calibrate and image**: JAO scripts, flux scaling to Butler-JPL-Horizons, uvcontsub, clean (Hogbom, natural)  
  > "Imaging and deconvolution were performed using the `clean` task; the point-spread function was deconvolved using the Hogbom algorithm, with natural visibility weighting" (Observations)
   - software: CASA
   - parameter: threshold 18 mJy; pixel 0.1''  
  > "The image pixel size was set to $0.1''\times0.1''$" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **extract disk-averaged spectrum and moment maps**: Integrate over elliptical region enclosing 90% of continuum flux; maps by integrating line widths  
  > "defining a pixel mask based on a flux threshold, which was varied until 90% of the total continuum flux was enclosed." (Results)
   - software: CASA
   - parameter: ellipse FWHM 2.3'' x 1.5''  
  > "an elliptical region (with FWHM $2.3''\times1.5''$)" (Results)
   - fitting: _not stated_
   - validation: Compared with 100% aperture; difference negligible  
  > "The difference in line-to-continuum ratio for this region compared with a larger extraction aperture including 100% of the detected flux was found to be negligible" (Results)
3. **retrieve vertical abundance profiles**: NEMESIS line-by-line radiative transfer with step (300 km) models for C2H3CN/C2H5CN and fractional scale-height gradient models for HC3N/CH3CN; spectra scaled to model in line-free regions  
  > "The abundances and fractional scale-height parameters $f_H$ were optimized by minimizing the sum of squares of the spectroscopic residuals" (Results)
   - software: NEMESIS
   - parameter: 35 impact parameters up to 1000 km; Lorentz width 0.075 cm-1/bar, alpha 0.5 (HC3N 0.1, 0.75)  
  > "across 35 impact parameters between the center of Titan’s disk and the top of the model atmosphere at 1000 km" (Results)
   - assumption: temperature profile from HASI+CIRS feathered 60-100 km; CO abundance 5.06e-5  
  > "by feathering the profiles together in the range 60-100 km using a linearly graded (weighted) average." (Results)
   - fitting: least squares minimization of residuals  
  > "optimized by minimizing the sum of squares of the spectroscopic residuals" (Results)
   - validation: reduced chi-squared; step heights >200 km acceptable  
  > "we find that models with a step height of $>$200 km provide a reasonable fit to our C$_2$H$_3$CN and C$_2$H$_5$CN observations" (Results)
4. **fit latitudinal flux profiles**: Two-component Gaussians, FWHM fixed at 4600 km  
  > "Two-component Gaussian fits with freely variable positions and intensities for the Gaussian components have been performed to these profiles, but with FWHM fixed at the instrumental resolution of 4600 km." (Discussion)
   - fitting: free positions and intensities  
  > "Two-component Gaussian fits with freely variable positions and intensities for the Gaussian components have been performed to these profiles, but with FWHM fixed at the instrumental resolution of 4600 km." (Discussion)
   - validation: assessed temperature effect <20% HC3N, <10% CH3CN  
  > "The resulting temperature dependence of our detected emission line strengths was found to be $<20$% for HC$_3$N, $<10$% for CH$_3$CN, and negligible for the other species." (Discussion)

## Software

- **CASA** 4.5.3: calibration, uvcontsub, clean imaging  
  > "processed in the NRAO CASA software (version 4.5.3)" (Observations)
- **NEMESIS** : radiative transfer and abundance retrieval  
  > "line-by-line radiative transfer module of the NEMESIS atmospheric retrieval code (cite: irw08)" (Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| C2H3CN abundance (300 km step) | 3.03 | 0.29 | ppb | 3 | / C$_2$H$_3$CN /   3.03 (0.29)   / |
| C2H5CN abundance (300 km step) | 7.37 | 0.32 | ppb | 3 | / C$_2$H$_5$CN /   7.37 (0.32)   / |
| C2H5CN/C2H3CN ratio | 2.43 | 0.26 | dimensionless | 3 | The C$_2$H$_5$CN/C$_2$H$_3$CN abundance ratio of $2.43\pm0.26$ |
| HC3N fractional scale-height | 2.05 | 0.16 | dimensionless | 3 | $2.05\pm0.16$ and $1.63\pm0.02$, respectively. |
| CH3CN fractional scale-height | 1.63 | 0.02 | dimensionless | 3 | $2.05\pm0.16$ and $1.63\pm0.02$, respectively. |
| C3H8 mixing ratio | 8.5e-7 | 0.6e-7 | mixing ratio | 3 | best-fitting C$_3$H$_8$ mixing ratio of $(8.5\pm0.6)\times10^{-7}$ |
| South/North flux ratio C2H3CN | 2.83 | 0.77 | dimensionless | 4 | / C$_2$H$_3$CN / -2569 (302) / 2842 (770) /  2.83 (0.77)  / |
| South/North flux ratio CH3CN | 0.67 | 0.02 | dimensionless | 4 | / CH$_3$CN     / -1930 (98)  / 2096 (60)  /  0.67 (0.02)  / |

## Qualitative findings

- C2H3CN, C2H5CN and HC3N concentrated at south pole; CH3CN in north  
  > "C$_2$H$_3$CN is most abundant over the southern (winter) pole, whereas the longer-lived CH$_3$CN is more concentrated in the north." (abstract)

## Claim tuples

- H: C2H3CN is detectable in Band 7 and can be mapped | E: Imaged archival ALMA Band 7 Titan data | R: Three firm lines detected plus one tentative; map shows 5 sigma southern peak | F: First spatial map of C2H3CN, south-polar enriched | **supported**
- H: Propane is detectable at radio wavelengths | E: Modeled two C3H8 lines with NEMESIS | R: Reduced chi2 1.06 vs 1.73 without; lines blended | F: Tentative detection only | **partially**
- H: Nitrile distribution reflects circulation reversal and differing lifetimes | E: Latitudinal flux profiles with Gaussian fits | R: South enhancement for HC3N, C2H3CN, C2H5CN; CH3CN northern | F: Consistent with circulation reversal and shorter lifetimes of unsaturated species | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gradient or different-cutoff step models also fit C2H3CN/C2H5CN; 300 km chosen for comparison with Palmer et al.  
  > "we adopt 300 km here to facilitate comparison with the results of (cite: pal17)." (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): C3H8 lines blended so abundance uncertain; south pole partly hidden  
  > "our fitted value should be treated with extreme caution due to the fact that the two propane lines are both blended" (Results)
- Caveat (inferred, ours): Single 3-minute observation, one epoch
- Caveat (inferred, ours): Step-model abundances non-unique
- Caveat (inferred, ours): Spatial resolution comparable to Titan's disk limits mapping
- Caveat (inferred, ours): Gaussian fits with fixed FWHM are crude

## Reproducibility

- Data public (paper): Data from ALMA Science Archive  
  > "we present new higher-sensitivity sub-mm data obtained from the ALMA Science Archive." (Introduction)
- Products in archive: _not stated_
- Missing: CIRS temperature profile
- Missing: NEMESIS setup files and priors/initial values
- Missing: line-free channels and integration ranges
- Data volume (inferred): ~1-5 GB
- Score (inferred): 3/5, Public data and named software, but NEMESIS inputs and several imaging details are missing.
- Rediscovery candidate: no, Retrieval requires NEMESIS and CIRS temperature inputs not fully provided.

## Links

- Method: Irwin et al. 2008 (cite: irw08) (NEMESIS code)
- Method: Cordiner et al. 2015 (cite: cor15) (ALMA Titan processing methodology)
- Companion: Palmer et al. 2017 (cite: pal17) (initial C2H3CN detection with ALMA)

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
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
  "facts": 74,
  "stated": 46,
  "rate": 0.622
 },
 "evidence_ok": true
}
```
