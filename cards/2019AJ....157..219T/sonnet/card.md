# Measurement of CH<SUB>3</SUB>D on Titan at Submillimeter Wavelengths

`2019AJ....157..219T` | The Astronomical Journal 2019 | first author: Thelen, Alexander E. | arXiv: 1905.00576 | DOI: 10.3847/1538-3881/ab19bb

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: solar_system
- Question: Can CH3D be detected in Titan's atmosphere at submillimeter wavelengths with ALMA, and what disk-averaged CH3D abundance and D/H in CH4 does it imply?  
  > "We present the first radio/submillimeter detection of monodeuterated methane (CH$_3$D) in Titan’s atmosphere" (abstract)
- Target **Titan**: coordinates _not stated_; z/distance 9.038 AU  
  > "Radiances were converted using Titan’s distance of 9.038 AU." (3 Radiative Transfer Modeling); "these values were obtained from the JPL Horizons ephemerides generator" (3 Radiative Transfer Modeling); distance from JPL Horizons ephemerides  
  > "Radiances were converted using Titan’s distance of 9.038 AU." (3 Radiative Transfer Modeling); "these values were obtained from the JPL Horizons ephemerides generator" (3 Radiative Transfer Modeling)

## Data provenance

- ALMA projects: 2013.1.00227.S, 2013.1.01010.S, 2012.1.00688.S
- bands: Band 8 (~385-500 GHz)  
  > "As of 2015, ALMA Band 8 ($\sim385-500$ GHz) has been available for use" (2 Observations)
- frequencies and spectral setup: 3904 kHz resolution; CH3D J=2-1 lines at 465.235 and 465.250 GHz  
  > "Despite the somewhat coarse spectral resolution inherent to these data (3904 kHz)" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam 0.767x0.491 arcsec  
  > "The beam full width at half maximum (FWHM) = $0.767\times0.491''$ for this observation" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~157 s typical for Titan flux calibration observations  
  > "resulting in many short ($\sim157$ s) observations of the moon from 2012 onward" (2 Observations)
- observing dates: 2015 May 02, UT 03:57:08  
  > "an observation on 2015 May 02 at UT 03:57:08" (2 Observations)
- pi or archival as stated: Archival ALMA flux calibration data  
  > "Using archival ALMA flux calibration data of Titan from 2015" (4 Discussion and Conclusions)
- Line: CH3D J_K=2_1-1_1 (465.235 GHz)
- Line: CH3D J_K=2_0-1_0 (465.250 GHz)
- Other facility **Cassini-Huygens GCMS**: CH4 vertical abundance profile used to derive D/H  
  > "By comparison with the CH$_4$ vertical abundance profile measured by *Cassini-Huygens* mass spectrometry" (abstract)
- External data: CH4 and N2 vertical abundance profiles  
  > "We thus include N$_2$ and CH$_4$ vertical abundance profiles from (cite: niemann_10) and (cite: teanby_13)" (3 Radiative Transfer Modeling) [from (cite: niemann_10); (cite: teanby_13)]
- External data: CH3D line and partition function parameters from CDMS  
  > "CH$_3$D spectral line and partition function parameters were obtained from the Cologne Database for Molecular Spectroscopy" (3 Radiative Transfer Modeling) [from (cite: muller_01; womack_96; bray_17)]
- External data: Line broadening coefficients from HITRAN 2012  
  > "Line broadening and temperature dependence coefficients were obtained from the HITRAN 2012 database" (3 Radiative Transfer Modeling) [from (cite: rothman_13)]
- External data: HC3N 2015 disk-averaged abundance profile  
  > "HC$_3$N, using the 2015 disk-averaged abundance profile found in (cite: thelen_19)" (3 Radiative Transfer Modeling) [from (cite: thelen_19)]
- External data: Stratospheric temperature profile from contemporaneous ALMA measurements  
  > "using contemporaneous ALMA measurements from (cite: thelen_18) in the stratosphere and above" (3 Radiative Transfer Modeling) [from (cite: thelen_18)]

## Processing

### Calibration

- pipeline or manual: Re-ran ALMA calibration scripts from the archive, avoiding flagging of Titan lines, with updated Titan flux model  
  > "we re-ran the ALMA data calibration scripts available with raw data from the ALMA Science Archive" (2 Observations)
- casa version: CASA 5.1.2  
  > "Using the Common Astronomy Software Applications (CASA) package version 5.1.2" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan, updated flux model (ALMA Memo 594)  
  > "to include the updated flux model for Titan (see ALMA Memo $\#$594" (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: Högbom clean  
  > "Imaging was completed using the `Hogb``ö``m clean` algorithm" (2 Observations)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.1x0.1 arcsec  
  > "with a pixel size = $0.1\times0.1''$ and a flux threshold of 10 mJy" (2 Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.767x0.491 arcsec FWHM  
  > "The beam full width at half maximum (FWHM) = $0.767\times0.491''$ for this observation" (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Method for disk-averaged spectra and calibrated cubes from ALMA Titan flux calibration data  
  > "We followed the methodology described in previous works utilizing ALMA flux calibration data of Titan" (2 Observations) [from (cite: cordiner_14; lai_17; thelen_18; thelen_19)]
- Mask of pixels containing at least 90% of Titan's continuum flux  
  > "defining a mask of pixels containing at least $90\%$ of Titan’s continuum flux, as in (cite: lai_17)" (3 Radiative Transfer Modeling) [from (cite: lai_17)]
- Flux to radiance conversion  
  > "as described in Appendix A of (cite: teanby_13)" (3 Radiative Transfer Modeling) [from (cite: teanby_13)]

### Not stated but needed to reproduce (our reading)

- Which ALMA execution block/MS and which calibrator/scripts exactly
- Clean mask and number of iterations; weighting scheme
- Line-free channels and continuum subtraction method
- Pixel mask definition details and how noise/significance was computed
- Error treatment behind the +-0.081e-4 D/H
- How the 1.047 scale factor was derived exactly
- Full temperature profile values

## Analysis recipe

1. **Calibrate and image**: Re-ran archive calibration scripts in CASA with updated Titan flux model; Högbom clean imaging  
  > "we re-ran the ALMA data calibration scripts available with raw data from the ALMA Science Archive" (2 Observations)
   - software: CASA
   - parameter: pixel 0.1 arcsec, threshold 10 mJy  
  > "with a pixel size = $0.1\times0.1''$ and a flux threshold of 10 mJy" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract disk-averaged spectrum and convert to radiance**: Mask of pixels with >=90% of continuum flux; convert flux density to radiance using 24 line-of-sight emission angles up to 1200 km  
  > "using 24 line of sight emission angles to model the flux from the full disk of Titan and the atmosphere up to 1200 km above the surface" (3 Radiative Transfer Modeling)
   - software: NEMESIS
   - parameter: distance 9.038 AU; sub-observer latitude 24.55 deg; Doppler shift -7.5 km/s  
  > "The sub-observer latitude was $24.55^\circ$ and the Doppler shift was $-7.5$ km s$^{-1}$" (3 Radiative Transfer Modeling)
   - fitting: _not stated_
   - validation: 24 annuli sufficient for disk-averaged radiance  
  > "summing over 24 annuli was sufficient to model the disk-averaged radiance from these data" (3 Radiative Transfer Modeling)
3. **Model continuum and set offset**: CIA continuum from CH4, H2, N2; temperature profile from ALMA stratosphere plus HASI/radio occultation troposphere; data scaled by 1.047  
  > "rectified by multiplying the data by a factor of 1.047" (3 Radiative Transfer Modeling)
   - software: NEMESIS
   - fitting: _not stated_
   - validation: Scaling consistent with previous ALMA flux-calibration studies  
  > "This scaling factor is consistent with previous studies using ALMA flux calibration data" (3 Radiative Transfer Modeling)
4. **Fit CH3D abundance**: Line-by-line NEMESIS with a constant multiplicative scaling of a priori CH3D profiles (CH4 times D/H from 1.13-1.59e-4); profile shape fixed, other parameters held constant  
  > "we opted to find a best-fit spectrum using a simple scaling model (i.e. a constant multiplicative factor) of an *a priori* CH$_3$D profile" (3 Radiative Transfer Modeling)
   - software: NEMESIS
   - parameter: CO 50 ppm constant  
  > "CO with a constant volume mixing ratio of 50 ppm" (3 Radiative Transfer Modeling)
   - assumption: CH3D profile follows CH4 Huygens GCMS profile shape  
  > "Our initial CH$_3$D profiles were found by multiplying *in situ* CH$_4$ data obtained with the *Huygens* probe" (3 Radiative Transfer Modeling)
   - fitting: Scaling factor fit; all a priori profiles converge on a single best fit  
  > "Models using all *a priori* abundance profiles converge on a single best-fit spectrum" (3 Radiative Transfer Modeling)
   - validation: _not stated_
5. **Derive D/H**: Compare CH3D abundance with GCMS CH4 profile  
  > "When taken with the CH$_4$ profile found by the *Huygens* GCMS (cite: niemann_10), our CH$_3$D abundance yields a D/H" (4 Discussion and Conclusions)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.2: calibration and imaging  
  > "Using the Common Astronomy Software Applications (CASA) package version 5.1.2" (2 Observations)
- **NEMESIS** : radiative transfer modeling and abundance fitting  
  > "using the Non-linear optimal Estimator for MultivariatE spectral analySIS (NEMESIS) software package" (3 Radiative Transfer Modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3D detection significance, J=2-1 line at 465.235 GHz | 4.6 | not stated | sigma | 0 | measured at significance levels of $4.6\sigma$ and $5.7\sigma$, respectively |
| CH3D detection significance, line at 465.250 GHz | 5.7 | not stated | sigma | 0 | measured at significance levels of $4.6\sigma$ and $5.7\sigma$, respectively |
| Disk-averaged CH3D volume mixing ratio | 6.157e-6 | not stated | dimensionless | 4 | disk-averaged CH$_3$D volume mixing ratio = $6.157\times10^{-6}$ in Titan’s stratosphere |
| D/H in CH4 | 1.033e-4 | 0.081e-4 | dimensionless | 5 | the resulting value for D/H in CH$_4$ is $(1.033\pm0.081)\times10^{-4}$ |
| Scale factor applied to data | 1.047 | not stated | dimensionless | 3 | rectified by multiplying the data by a factor of 1.047 |
| New weighted mean Cassini-era D/H | 1.203e-4 | +0.057/-0.054 e-4 | dimensionless | 5 | new weighted mean D/H = ($1.203^{+0.057}_{-0.054})\times10^{-4}$ |

## Qualitative findings

- No significant pole-to-pole variation (<~30%) of CH3D in the integrated flux map, though resolution and S/N are too low to interpret latitudinal variations  
  > "shows a lack of significant variation between the poles (less than $\sim30\%$)" (4 Discussion and Conclusions)

## Claim tuples

- H: CH3D can be detected at submm wavelengths in Titan with ALMA | E: Analysis of archival Band 8 flux calibration data | R: Two J=2-1 lines at 4.6 and 5.7 sigma | F: First definitive submm detection of CH3D on Titan | **supported**
- H: ALMA-derived D/H agrees with previous measurements | E: NEMESIS fit of CH3D combined with GCMS CH4 | R: D/H = (1.033+-0.081)e-4 | F: Consistent with previous measurements though lower than the Cassini-era average; to be taken with caution | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Simple scaling model chosen due to coarse spectral resolution and low S/N  
  > "Due to the somewhat coarse spectral resolution settings of this observation and the relatively low signal-to-noise ratio of both CH$_3$D lines" (3 Radiative Transfer Modeling)
- Alternative: Extracting flux within 2x the ALMA PSF was rejected because it diluted the disk-averaged CH3D lines  
  > "resulted in a dilution of the disk-averaged CH$_3$D lines in these data" (3 Radiative Transfer Modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): Error bars reflect only retrieval errors; disk-averaged ALMA data not directly comparable to the equatorial GCMS CH4; only one suitable dataset so no stacking  
  > "The error bars on our measurement are relative, and only reflect the retrieval errors of our best-fit synthetic CH$_3$D spectrum." (4 Discussion and Conclusions)
- Caveat (inferred, ours): D/H depends strongly on assumed CH4 profile (GCMS equatorial vs disk-average)
- Caveat (inferred, ours): Low S/N and coarse resolution; only constant scaling fit
- Caveat (inferred, ours): Uncertainty excludes systematic errors (temperature, flux scale)

## Reproducibility

- Data public (paper): Archival ALMA data from the ALMA Science Archive  
  > "we re-ran the ALMA data calibration scripts available with raw data from the ALMA Science Archive" (2 Observations)
- Products in archive: _not stated_
- Missing: Exact clean parameters and masks
- Missing: Fitted temperature and abundance profile tables
- Missing: Details of uncertainty derivation
- Data volume (inferred): ~1-5 GB (one short Band 8 execution)
- Score (inferred): 3/5, Public data and software are named, but several imaging and modeling details are missing or deferred to earlier papers.
- Rediscovery candidate: yes, Data are public, the recipe is mostly described, and the results are numeric, though some details are missing.

## Links

- Method: (cite: irwin_08) (NEMESIS retrieval code)
- Method: (cite: teanby_13) (flux to radiance conversion)
- Method: (cite: lai_17) (disk-averaging mask method)
- Companion: (cite: thelen_18) (earlier ALMA Titan analysis, temperature profile)
- Companion: (cite: thelen_19) (contemporaneous ALMA Titan data, HC3N profile)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2012.1.00688.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 43,
  "rate": 0.566
 },
 "evidence_ok": true
}
```
